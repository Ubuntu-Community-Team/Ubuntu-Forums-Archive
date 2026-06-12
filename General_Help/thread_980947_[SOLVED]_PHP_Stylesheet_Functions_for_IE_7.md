---
title: "[SOLVED] PHP Stylesheet Functions for IE 7"
date: 2008-11-13
forum: General Help
---

### Post by CrusaderAD on 2008-11-13
Does anyone know of a good link to some information on Internet Explorer 7 php stylesheet functions? I have a style sheet that makes my web page look beautiful in all browsers except IE 7. Any help please?

---

### Post by Sam on 2008-11-13
PHP and stylesheets are two unrelated things.

If you have issues with IE7, you may create a IE7 only stylesheet:
```
<!--[if gte IE 7]><link href="ie_7.css" rel="stylesheet" type="text/css"><![endif]-->
```

Have a look there: [http://www.webdevout.net/css-hacks](http://www.webdevout.net/css-hacks)

---

### Post by CrusaderAD on 2008-11-13
Thanks that helped a lot! Can I do that for each browser? What's the code for other browsers? Like Internet Explorer 7 is IE 7.

---

### Post by CrusaderAD on 2008-11-13
Actually, it's a stylesheet implemented within a PHP index. This code doesn't seem to work, it's commented out. From what I read... it's supposed to be but IE doesn't change when I update the other stylesheet.

---

### Post by CrusaderAD on 2008-11-13
I tried this in my code...

<?php $browser = $_SERVER['HTTP_USER_AGENT']; ?>  
<?php if (strstr($browser, "MSIE")) { ?>  
<link rel="stylesheet" href="ie7.css" type="text/css" media="screen" />  
<?php }else{ ?>  
<link rel="stylesheet" href="default.css" type="text/css" media="screen" />  
<?php } ?>

Updating the ie7.css file doesn't change the way IE displays the page.

---

### Post by CrusaderAD on 2008-11-13
I works now, the previous code was fine... I was refreshing the browser wrong... doh!

---

