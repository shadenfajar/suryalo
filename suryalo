<?php
 
/**
 * Thanks To : Janu Yoga & Aan Ahmad
 * Date Share : 27-03-2019 (First Share)
 * Date Updated V.5 : 29-Agustus-2019
 * Created By : Will Pratama - facebook.com/yaelahhwil
**/
 
date_default_timezone_set("Asia/Jakarta");
class Marlboro extends modules
{
        public $fileCookies = "cookiesMarlboro.txt";
        protected $cookie;
        protected $modules;
 
        public function __construct()
        {
                $this->modules = new modules();
        }
 
        private function cookiesAkun()
        {
                $file = $this->fileCookies;
                foreach(explode("\n", str_replace("\r", "", file_get_contents($file))) as $a => $data)
                {
                        $pecah = explode("|", trim($data));
                        return array("cookie" => $pecah[0], "email" => $pecah[1], "password" => $pecah[2], "deviceid" => $pecah[3]);
                }
        }
 
        protected function login($email, $password)
        {
                if(@file_exists($this->fileCookies) == true)
                {
                        @unlink($this->fileCookies);
                }
 
                $cook = $this->modules->fetchCookies($this->modules->curl("https://www.marlboro.id", null, array("Host: www.marlboro.id"), 'GET')[1]);
                $headers = array();
                $headers[] = "Content-Type: application/x-www-form-urlencoded; charset=UTF-8";
                $headers[] = "Cookie: decide_session=".$cook['decide_session'];
                $headers[] = "X-Requested-With: XMLHttpRequest";
                $csrf = $this->modules->getStr($this->modules->curl("https://www.marlboro.id", null, $headers, 'GET')[0], 'name="decide_csrf" value="', '"', 1, 0);
                $login = $this->modules->curl("https://www.marlboro.id/auth/login", "email=".str_replace("@", "%40", $email)."&password=".$password."&ref_uri=%2F&decide_csrf=".$csrf."&param=&exception_redirect=false", $headers);
                $cookies = $this->modules->fetchCookies($login[1])['decide_session'];
                $deviceid = $this->modules->fetchCookies($login[1])['deviceId'];
            $this->modules->fwrite($this->fileCookies, trim($cookies)."|".$email."|".$password."|".trim($deviceid));
                return $login;
        }
 
        private function idVidio()
        {
                $headers = array();
                $headers[] = "Content-Type: application/x-www-form-urlencoded; charset=UTF-8";
                $headers[] = "Cookie: deviceId=".$this->cookiesAkun()['deviceid']."; decide_session=".$this->cookiesAkun()['cookie'];
                $headers[] = "Host: www.marlboro.id";
                $listIdVidio = $this->modules->curl("https://www.marlboro.id", null, $headers, 'GET');
                return $listIdVidio[0];
        }
 
        protected function view($idVidio)
        {
                $headers = array();
                $headers[] = "Content-Type: application/x-www-form-urlencoded; charset=UTF-8";
                $headers[] = "Cookie: deviceId=".$this->cookiesAkun()['deviceid']."; _ga=GA1.2.80096599.1559215776; _gid=GA1.2.79762902.1559215776; ins-mig-done=1; ev=1; _mm3rm4bre_=6B%2FUJWvPEfAWe0iZqDpXOJ1YF8gkcXhrMXVyJC5tajloaHdpamgwem1uYnhrdmlldjQ%3D; accC=true; mp_41fb5b1708a7763a1be4054da0f74d65_mixpanel=%7B%22distinct_id%22%3A%20%2216b0880a02b18f-066b2c15aa7e45-e353165-100200-16b0880a02c862%22%2C%22%24device_id%22%3A%20%2216b0880a02b18f-066b2c15aa7e45-e353165-100200-16b0880a02c862%22%2C%22%24initial_referrer%22%3A%20%22%24direct%22%2C%22%24initial_referring_domain%22%3A%20%22%24direct%22%7D; content_viewc=3; token=JeLy0F7pzJK722MQXeXVcxqbZSdTNxOX; refresh_token=0nvFDJuHhlQ7gb5x21X5GUfzdpnM2vPz; _gat_UA-102334128-3=1; decide_session=".$this->cookiesAkun()['cookie'];
                $headers[] = "Host: www.marlboro.id";
                $headers[] = "User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW".rand(000, 999).") AppleWebKit/".rand(00000, 99999).".36 (KHTML, like Gecko) Chrome/72.0.".rand(00000, 99999).".".rand(00000, 99999)." Safari/".rand(00000, 99999).".36";
                $headers[] = "X-Requested-With: XMLHttpRequest";
                $csrf = $this->modules->getStr($this->modules->curl("https://www.marlboro.id/", null, $headers, 'GET')[0], 'name="decide_csrf" value="', '"', 1, 0);
                $view = $this->modules->curl("https://www.marlboro.id/article/video-play/".$idVidio, "decide_csrf=".$csrf."&log_id=false&duration=0.007&total_duration=0&fetch=1&g-recaptcha-response=", $headers);
                return $view;
        }
 
        protected function update($idVidio, $decide_session, $log_id)
        {
                $headers = array();
                $headers[] = "Content-Type: application/x-www-form-urlencoded; charset=UTF-8";
                $headers[] = "Cookie: deviceId=".$this->cookiesAkun()['deviceid']."; _ga=GA1.2.80096599.1559215776; _gid=GA1.2.79762902.1559215776; ins-mig-done=1; ev=1; _mm3rm4bre_=6B%2FUJWvPEfAWe0iZqDpXOJ1YF8gkcXhrMXVyJC5tajloaHdpamgwem1uYnhrdmlldjQ%3D; accC=true; mp_41fb5b1708a7763a1be4054da0f74d65_mixpanel=%7B%22distinct_id%22%3A%20%2216b0880a02b18f-066b2c15aa7e45-e353165-100200-16b0880a02c862%22%2C%22%24device_id%22%3A%20%2216b0880a02b18f-066b2c15aa7e45-e353165-100200-16b0880a02c862%22%2C%22%24initial_referrer%22%3A%20%22%24direct%22%2C%22%24initial_referring_domain%22%3A%20%22%24direct%22%7D; content_viewc=3; token=JeLy0F7pzJK722MQXeXVcxqbZSdTNxOX; refresh_token=0nvFDJuHhlQ7gb5x21X5GUfzdpnM2vPz; _gat_UA-102334128-3=1; decide_session=".$this->cookiesAkun()['cookie'];
                $headers[] = "Host: www.marlboro.id";
                $headers[] = "Origin: https://www.marlboro.id";
                $headers[] = "Referer: https://www.marlboro.id/";
                $headers[] = "User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW".rand(000, 999).") AppleWebKit/".rand(00000, 99999).".36 (KHTML, like Gecko) Chrome/72.0.".rand(00000, 99999).".".rand(00000, 99999)." Safari/".rand(00000, 99999).".36";
                $headers[] = "X-Requested-With: XMLHttpRequest";
                $csrf = $this->modules->getStr($this->modules->curl("https://www.marlboro.id/", null, $headers, 'GET')[0], 'name="decide_csrf" value="', '"', 1, 0);
                $update = $this->modules->curl("https://www.marlboro.id/article/video-play/".$idVidio, "decide_csrf=".$csrf."&log_id=".$log_id."&duration=11.113&total_duration=5&fetch=2&g-recaptcha-response=", $headers);
                return $update[0];
        }
 
        private function getPoint()
        {
                $headers = array();
                $headers[] = "Content-Type: application/x-www-form-urlencoded; charset=UTF-8";
                $headers[] = "Cookie: "."deviceId=".$this->cookiesAkun()['deviceid']."; decide_session=".$this->cookiesAkun()['cookie'];
                $headers[] = "Host: www.marlboro.id";
                $get = $this->modules->curl("https://www.marlboro.id/profile", null, $headers, 'GET');
                return trim(@$this->modules->getStr($get[0], '<div class="point">', '</div>', 1, 0));
        }
 
        public function execute_login($email, $password)
        {
                for($o=1;$o<=10;$o++)
                {
                        @$pointAwal = $this->getPoint();
                        $login = $this->login($email, $password);
                        @$cookies = trim($this->modules->fetchCookies($login[1])['decide_session']);
                        @$deviceid = trim($this->modules->fetchCookies($login[1])['deviceId']);
                        if(strpos($login[0], '"code":200,"message":"success"'))
                        {
                                $this->modules->fwrite($this->fileCookies, @$cookies."|".$email."|".$password."|".$deviceid);
                                if(@$this->getPoint() == $pointAwal)
                                {
                                        print PHP_EOL."Success Login!, Limit Get Point Login... Done : ".$this->getPoint()." Pts";
                                        return false;
                                }else{
                                        print PHP_EOL."Success Login!, Point Anda : ".$this->getPoint()." Pts";
                                }
                        }elseif(strpos($login[0], '"message":"Please Accept GoAheadPeople T&C"')){
                                print PHP_EOL."Failed Login!, Message : Please Accept GoAheadPeople T&C.. Retry!";
                        }else{
                                if(@file_exists($this->fileCookies) == true)
                                {
                                        @unlink($this->fileCookies);
                                }
                                print PHP_EOL."Failed Login";
                                return false;
                        }
                }
        }
 
        public function execute_nonton($email)
        {
                if(@file_exists($this->fileCookies) == false){
                        return false;
                }
                print PHP_EOL."Mencoba Bot Nonton..";
                $ya = 1;
                for($b = $ya; $b <= ($ya + 20); $b++)
                {      
                        if($b%2 == 1)
                        {
                                @$pointAwal = $this->getPoint();
                                $idVidio = $this->modules->getStr($this->idVidio(), 'data-ref="https://www.marlboro.id/maze-of-decision/article/', '"', $b, 0);
                                if(!empty($idVidio))
                                {
                                        $view = $this->view($idVidio);
                                        $decide_session = trim($this->modules->fetchCookies($view[1])['decide_session']);
                                        $log_id = $this->getStr($view[0], '"log_id":"', '"', 1, 0);
                                        if(strpos($view[0], '"message":"Success to store log play video."'))
                                        {
                                                //print PHP_EOL."Sedang Menonton : ".$idVidio;
                                                $update = $this->update($idVidio, $decide_session, $log_id);
                                                if(strpos($update, '"finished":true'))
                                                {
                                                        if(@$this->getPoint() == @$pointAwal)
                                                        {
                                                                print PHP_EOL."Limit Get Point Nonton!,  Done : ".$email." | ".$this->getPoint()." Pts";
                                                                return false;
                                                        }else{ 
                                                                print PHP_EOL."Success Menonton!, Point anda : ".$this->getPoint()." Pts";
                                                        }      
                                                }else{
                                                        print PHP_EOL."Failed!, Point Anda : ".$this->getPoint().PHP_EOL.$update;
                                                }
                                        }elseif(strpos($view[0], '"message":"Action is not allowed"')){
                                                print PHP_EOL."Failed Menonton Vidio!, Message : Action is not allowed..";
                                                return false;
                                        }else{
                                                print PHP_EOL."Gagal Menonton ".$view[0];
                                        }      
                                }else{
                                        print PHP_EOL."ID Vidio Tidak Ditemukan..";
                                        return false;
                                }
                        }
                }      
        }
 
        public function bonusPoints()
        {
                if(@file_exists($this->fileCookies) == false){
                        return false;
                }
                print PHP_EOL."Mencoba Mendapatkan Bonus Points..";
                @$pointAwal = $this->getPoint();
                $url = 'https://www.marlboro.id/auth/update-profile';
                $headers = explode("\n","Host: www.marlboro.id\nContent-Type: application/x-www-form-urlencoded; charset=UTF-8\nX-Requested-With: XMLHttpRequest\nCookie: deviceId=".$this->cookiesAkun()['deviceid']."; decide_session=".$this->cookiesAkun()['cookie'].";");
                $csrf = $this->modules->getStr($this->modules->curl("https://www.marlboro.id", null, $headers, 'GET')[0], 'name="decide_csrf" value="', '"', 1, 0);
                $post = 'decide_csrf='.$csrf.'&email=&password=&phone_number=0&city=99&address=jalan+kangen+nomor+rindu+opit+kapan+bagi+ladang&old_password_chg=&new_password_chg=&confirm_password_chg=&security_question=500001002&security_answer=anjinsg&fav_brand1=500019562&fav_brand2=500019457&interest_raw=Visual&province=6&postalcode=0&interest=Visual&stop_subscribe_email_promo=false';
                $bonusPoints = $this->curl($url, $post, $headers);
                if(strpos($bonusPoints[0], '"message":"Update profile Success"'))
                {
                        if($pointAwal == $this->getPoint())
                        {
                                print PHP_EOL."Gagal Mendapatkan Bonus Point.. ".$this->getPoint()." Pts";
                        }else{
                                print PHP_EOL."Sukses Mendapatkan Bonus Point.. ".$this->getPoint()." Pts";
                        }
                }else{
                        print PHP_EOL."Gagalss Mendapatkan Bonus Point.. ".$this->getPoint()." Pts";
                }      
        }
 
}
 
class modules
{
        public function curl($url, $param, $headers, $request = 'POST')
        {
                $ch = curl_init();
                $data = array(
                                CURLOPT_URL                             => $url,
                                CURLOPT_POSTFIELDS              => $param,
                                CURLOPT_HTTPHEADER              => $headers,
                                CURLOPT_CUSTOMREQUEST   => $request,
                                CURLOPT_HEADER                  => true,
                                CURLOPT_RETURNTRANSFER  => true,
                                CURLOPT_FOLLOWLOCATION  => true,
                                CURLOPT_SSL_VERIFYPEER  => false
                        );
                curl_setopt_array($ch, $data);
                $execute = curl_exec($ch);
                $header_size = curl_getinfo($ch, CURLINFO_HEADER_SIZE);
                $header = substr($execute, 0, $header_size);
                $body = substr($execute, $header_size);
                curl_close($ch);
                return [$body, $header];
        }
 
        public function getStr($page, $str1, $str2, $line_str2, $line)
        {
                $get = explode($str1, $page);
                $get2 = explode($str2, $get[$line_str2]);
                return $get2[$line];
        }
 
        public function fetchCookies($source)
        {
                preg_match_all('/^Set-Cookie:\s*([^;]*)/mi', $source, $matches);
                $cookies = array();
                foreach($matches[1] as $item)
                {
                        parse_str($item, $cookie);
                        $cookies = array_merge($cookies, $cookie);
                }
 
                return $cookies;
        }
 
        public function fwrite($namafile, $data)
        {
                $fh = fopen($namafile, "a");
                fwrite($fh, $data);
                fclose($fh);  
        }
}      
 
$modules = new modules();
$marlboro = new marlboro();
 
print "\n[!] Script Created By: Will Pratama";
print "\n[!] Note: Jangan Run Lebih Dari 1 Terminal, Kecuali File Beda Folder!";
print "\n[!] Note: Diusahakan menggunakan IP Indonesia";
print "\n[!] @Version: V.5\n\n";
 
print "Bonus 250 Points? (Khusus Akun Baru) y/n : ";
$bonus = trim(fgets(STDIN));
 
awal:
echo "Input FIle Akun Marlboro (Email|Pass) : ";
$fileakun = trim(fgets(STDIN));
 
if(empty(@file_get_contents($fileakun)))
{
        print PHP_EOL."File Akun Tidak Ditemukan.. Silahkan Input Ulang".PHP_EOL;
        goto awal;
}
 
print PHP_EOL."Total Ada : ".count(explode("\n", str_replace("\r","",@file_get_contents($fileakun))))." Akun, Letsgo..";
 
while(true)
{
        echo PHP_EOL."Start Date : ".date("Y-m-d H:i:s");
        foreach(explode("\n", str_replace("\r", "", @file_get_contents($fileakun))) as $c => $akon)
        {      
                $pecah = explode("|", trim($akon));
                $email = trim($pecah[0]);
                $password = trim($pecah[1]);
                echo PHP_EOL.PHP_EOL."Ekse Akun : ".$email.PHP_EOL;
 
                $marlboro->execute_login($email, $password);
                if($bonus == "y" or $bonus == "Y")
                {
                        $marlboro->bonusPoints();
                }
                $marlboro->execute_nonton($email);
        }
       
        echo PHP_EOL.PHP_EOL."Sleep Time : ".date("Y-m-d H:i:s");
        print PHP_EOL."All Done Run!, Sleep 24 Hours";
        print PHP_EOL."Start Besok : ".date('Y-m-d H:i:s', time() + (60 * 60 * 24));
        sleep(86400);
}
 
?>
