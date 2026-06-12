---
title: "apache problems"
date: 2008-09-14
forum: General Help
---

### Post by fedex1993 on 2008-09-14
Okay well i finally got my home server back up again but where having problems with apache2. Where using python for webtemplates as you would call it. Right now there is a file called index.py and we have the .htaccess to directory index of index.html index.py and index.php. we also have addhandler cgi-script .py. For some reason it will not load .py files but will load .php and .html files. Is there a reason why this is happeneing?

---

### Post by -Zeus- on 2008-09-14
do you have all the python packages installed?

---

### Post by fedex1993 on 2008-09-14
maybe i don't know is what python packages do i need?

---

### Post by fragos on 2008-09-15
For what it's worth here are the three lines for httpd.conf that are required to enable PHP in a default Apache2 install. Python is a very complete programming language and I'm not surprised that it requires configuration to be used by a web server as is the case with PHP. Therefore I'd expect something similar to the following for PHP:

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

I don't have Python enabled in my server so I'm unsure of the exact configuration statements. I did a search in Synaptic for "apache python" and found the following package that would appear to provide what you want "libapache2-mod-python".

---

