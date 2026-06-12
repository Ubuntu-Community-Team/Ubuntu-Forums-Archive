---
title: "how to open .php files with firefox browser? (Solved)"
date: 2005-11-15
forum: General Help
---

### Post by denvervp on 2005-11-15
I start to learn php and just wondering how to process .php files with firefox. Every time I link to a file with .php, it asks me to save or open with a text editor. (I have PHP, mySQL and Apache installed, followed the instructions at ubuntuguide.org)
Thanks.

---

### Post by manicka on 2005-11-15
My understanding is that .php only contain text data to tell the server how to render the page, hence they are trying to open in a text editor. This is normal.

---

### Post by Remmelas on 2005-11-15
May seem like a basic question, but, are you browsing the php file through apache, or straight from the filesystem?

---

### Post by denisesballs on 2005-11-15
Firefox won't just build the php code. That's what a web server is for. PHP is a server side language assembled by the web server, translated to (x)html, and _then_ interpreted by the browser. You'll have to install apache or something similar first to "serve" the code to the browser.

---

### Post by denvervp on 2005-11-15
Ok, I open firefox >>File>>OpenFile>>myfile.php
Maybe that's why. How do I open it thru Apache? Or how do I test my php scripts?

---

### Post by kimsay on 2005-11-15
[QUOTE=denvervp]Ok, I open firefox >>File>>OpenFile>>myfile.php
Maybe that's why. How do I open it thru Apache? Or how do I test my php scripts?[/QUOTE]

You must open a php file with apache. 
[http://localhost/myfile.php](http://localhost/myfile.php) or so... the files must save in the apache directory (htdocs)

---

### Post by denisesballs on 2005-11-15
[QUOTE=denvervp]Ok, I open firefox >>File>>OpenFile>>myfile.php
Maybe that's why. How do I open it thru Apache? Or how do I test my php scripts?[/QUOTE]

Install apache (apt-get install apache), make sure it's running (/etc/init.d/apache restart), and put whatever php files you want to test in /var/www . Then in firefox type localhost in the address bar.

---

### Post by aysiu on 2005-11-15
[QUOTE=denisesballs]Install apache (apt-get install apache), make sure it's running (/etc/init.d/apache restart), and put whatever php files you want to test in /var/www . Then in firefox type localhost in the address bar.[/QUOTE] Awesome! Works for me. By the way, instead of actually *putting* my test files in /var/www, I created a symlink from my real test file location to /var/www, and it worked just fine. Thanks for the tip!

---

### Post by denvervp on 2005-11-15
Thanks for all your help. I got it.
Copy my php file to Apache default folder /var/www and load it with [http://localhost/myfile.php](http://localhost/myfile.php)
Thank you.

---

### Post by denisesballs on 2005-11-15
Cool, glad to help.Just be aware that you are a web server when apache is running, and should take security measures. Firewall etc.

---

