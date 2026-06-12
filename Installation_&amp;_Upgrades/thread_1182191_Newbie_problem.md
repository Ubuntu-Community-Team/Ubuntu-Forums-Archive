---
title: "Newbie problem"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by slindbla on 2009-06-08
I am trying desperately to install Ubuntu to run a PHP-application (Magento)
I have created an Ubuntu desktop 9.04 CD, and installation runs fine.
Then I install the Apache2, MySQL and PHP5 packages using the package manager.
 
I copy a PHP-file to a directory in my home-folder and sets all permissions to rwx
 
But when I try to open the PHP-file with Firefox it only asks if I want to open the file in an application or if I want to save it.
 
When I try "sudo a2enmod php5" in Terminal it says "Module PHP5 already enabled"
 
I have reinstalled my server a million times now, and I am getting pretty desperate...
 
HELP, please !!!

---

### Post by ManiDhillon on 2009-06-08
Try putting your php files in /var/www and then run [http://localhost](http://localhost) to execute it.

---

### Post by dyingsun on 2009-06-08
I have the same problem even when I put my files in var/www, and have changed the perms. The way I get around it is by not having an index file in the directory where I store my php files. I link to the various subdirectories with html starting at localhost, and when I use Firefox to navigate to my php directory, it can't find an index.html and so it just shows a listing of all the files in that subdirectory. Then I can just click on whichever php file I need to use and it opens properly in Firefox.

Im sure there's a way of doing it properly via nautilus or whatever, I just haven't had time lately to sort it out. Maybe it's some kind of Apache parsing problem, not sure, I'm not very experienced with server-side tech yet!

Anyway, how I'm doing it in the short term. During the holidays I'll look into it deeper and try to fix it.

---

### Post by slindbla on 2009-06-09
THANKS !!!
 
Moving it to /var/www worked !!!

---

### Post by stuart4487 on 2010-02-08
Try a track that looks like this:
    <track>
      <creator>Mike M</creator>
      <title>S K Y . F M - 80s, 80s, 80s! - Hear your classic favorites right here! (www.sky.fm)</title>
      <location>http://radio.netbynet.ru:8000/sky.fm.hit-80's</location>
      <meta rel="type">sound</meta>
      <info>http://www.sky.fm</info>
    </track>

---

