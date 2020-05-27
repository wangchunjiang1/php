1.  //随机获取电话号
function generate_name( $count, $type="array", $white_space=false)
{
 $arr = array(
 130,131,132,133,134,135,136,137,138,139,
 144,147,
 150,151,152,153,155,156,157,158,159,
 176,177,178,
 180,181,182,183,184,185,186,187,188,189,
);
 for($i = 0; $i < $count; $i++) {
  $tmp[] = $arr[array_rand($arr)].' '.mt_rand(1000,9999).' '.mt_rand(1000,9999);
 }
 if($type==="string"){
  $tmp=json_encode($tmp);//如果是字符串，解析成字符串
 }
 if($white_space===true){
  $tmp=preg_replace("/\s*/","",$tmp);
 }
 return $tmp;
}

2.  //上传文件函数，可以下载文件
function upload_file($base_img_url) {
 $end_name = substr($base_img_url,strrpos($base_img_url,'.'));
 $img_data = ['.jpg'=>1,'.jpeg'=>1,'.gif'=>1,'.png'=>1,'.bmp'=>1];//支持这些常规图片
 $if_have_img = isset($img_data[$end_name])?1:0;
 if($if_have_img == 0){
  $end_name = '.jpg';//如果是其他格式则默认为jpg
 }
 $img_str = file_get_contents($base_img_url);
 $imgbase64 = base64_encode($img_str);
 $imgbase64 = 'data:image/jpeg;base64,'.$imgbase64;
 $url1 = date("YmdHis").mt_rand(1000,9999).$end_name;
 $base64_string= explode(',', $imgbase64); //截取data:image/png;base64, 这个逗号后的字符
 $data1 = base64_decode(",".$base64_string[1]);//对截取后的字符使用base64_decode进行解码
 $new_data = date('Ymd',time());
 //文件上传
 $path = IMAGE_ROOT . "/imgs/shop/script/";//改成自己要上传的目录
 if(!is_dir($path)){
  mkdir($path,0777,true);
 }
 file_put_contents($path.$url1, $data1); //写入文件并保存
 $up_url = "/shop/script/".$url1;
 return $up_url;//改成自己要上传的目录
}
