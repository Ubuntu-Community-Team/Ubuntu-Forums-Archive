---
title: "How do I use php/mysql with Ubuntu?"
date: 2008-08-16
forum: General Help
---

### Post by DoctorBeaver on 2008-08-16
I am a complete beginner to Linux so please be gentle with me.

I had an old PC lying around with a corrupt XP OS on it so I thought I'd give Ubuntu a go as I'd heard lots of good things about it. I downloaded the latest version & after a couple of unsuccessful attempts managed to install it using safe graphics mode.

I do a lot of php/mysql development for my own websites and up until now I've been using JSAS under Windows to do all my work. Having played with Ubuntu a bit, I quite like it so would like to switch all my development work from Windows.

I read that most Linux distros come with php; however, I've done a search & I can't seem to find it anywhere (it might help if I knew what the Linux equivalent of a .exe file is!).

So, how do I set up my system to be able to use php/mysql? What do I need to do? Is there a package for Linux similar to JSAS that I can just install & off I go?

Any help in total idiot language would be much appreciated.

Thank you.

Doc.

---

### Post by eggdeng on 2008-08-16
Go to System -> Administration ->Synaptic Package Manager. You will be asked for your password.
Go to Edit and choose the option Mark packages by task
In the new dialogue, tick LAMP Server & then Install.
You will need to supply a root password for mysql during install.
Probably the easiest way to get everything started is by rebooting.
Open firefox, type localhost into the address bar and you should see a welcome message.
The web root directory where you put your html and php files is /var/www.
chmod -R 777 /var/www will give you the necessary permissions.

---

### Post by DoctorBeaver on 2008-08-16
eggdeng - Thanks for your help. I've done all that up to the chmod. How do I do that?

---

### Post by eggdeng on 2008-08-16
Open a terminal (Applications->Accessories->Terminal). Copy and paste the following
```
sudo chmod -R 777 /var/www
```
into the terminal and press Intro. Supply your password when prompted.

---

### Post by DoctorBeaver on 2008-08-17
eggdeng - That's great. It worked. Thank you for your help. Much appreciated.

Can I pick you brains again, though? What about mysql? How do I set that up?

---

### Post by Shunsuke_01 on 2008-08-17
Also, the "Ubuntu equivalent" of a .exe is a deb file if I can recall correctly.

Other linux distributions use other file extensions such as "rpm" for Fedora/Red Hat.

I've installed programs on Ubuntu using these deb files before, but I prefer to use the terminal anyway. ;)

---

### Post by eggdeng on 2008-08-17
Again, open a terminal and type
mysql -u root -p*password*
where *password* is the mysql root user password you created when you installed mysql. No whitespace between -p and *password*.
You can now create, grant and delete to your heart's content.
> That's great. It worked. Thank you for your help. Much appreciated.
If you are logged in, you can use the little blue medal icon at the bottom right of each post to mark it as helpful / thank the poster.
Glad to be of help.

---

### Post by az on 2008-08-17
See here:
[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)


If your web server is going to be accessed from the outside, it's not a good idea to chmod /var/www.  The webserver should not have write access to it.  Only very few directories should be writable by apache.  

If someone can exploit a vulnerability, they can gain access to your system that way.

---

### Post by DoctorBeaver on 2008-08-17
eggdeng & az - you've both been very helpful & it is much appreciated.

One last question - up until now I've been using php/myadmin to administer my mysql databases. What would be a good program to use under Ubuntu?

---

### Post by cariboo on 2008-08-17
You can use phpmyadmin to administer mysql. It is available in the repositories, you can use Add/Remove Programs,Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by az on 2008-08-17
> **DoctorBeaver said:**
> eggdeng & az - you've both been very helpful & it is much appreciated.

One last question - up until now I've been using php/myadmin to administer my mysql databases. What would be a good program to use under Ubuntu?

You can run phpmyadmin in Ubuntu.  Just install it.

sudo apt-get install phpmyadmin

---

### Post by DoctorBeaver on 2008-08-17
OK, I've done all that - but how do I run it (or any other program I install)? :confused: It doesn't show in the Applications menus

Sorry if I'm being a total dork, but I've never used Linux before.

---

### Post by az on 2008-08-17
> **DoctorBeaver said:**
> OK, I've done all that - but how do I run it (or any other program I install)? :confused: It doesn't show in the Applications menus

Sorry if I'm being a total dork, but I've never used Linux before.

Phpmyadmin is a web application.  It runs on your web server.  Browse your webserver and look in the phpmyadmin folder.  If you changed your default vhost, make one for the phpmyadmin folder.

---

### Post by eggdeng on 2008-08-17
Generally, you can run a program in linux just by typing its name in a terminal and hitting intro. Try, for example ```
mplayer
``` or ```
gedit
```
I have never installed phpmyadmin but as far as I can tell, the procedure is as follows. 
First, tell apache you want to use PHPMyAdmin
```
  gksudo gedit /etc/apache2/apache2.conf
```

At the bottom of the file, add
```
# Enable PHPMyAdmin
Include /etc/phpmyadmin/apache.conf
```

Save and close, then restart apache
```
sudo /etc/init.d/apache2 restart
```

You should now be able to access it by typing 127.0.0.1/phpmyadmin or localhost/phpmyadmin in the address bar of your browser.

These instructions are in the ubuntu guide at [http://ubuntuguide.org/wiki/Ubuntu:Hardy]("http://ubuntuguide.org/wiki/Ubuntu:Hardy") Take a look, I'm sure you will find it very useful.

---

### Post by DoctorBeaver on 2008-08-17
Thanks, AZ, I've got it. Now all I have to do is remember the default username & password for it

---

### Post by DoctorBeaver on 2008-08-18
I tried what I thought was the correct username & password, but still couldn't get it. I read in the documentation about changing the config.inc.php file.

I opened the file & it was empty. I added the following, as per the instructions:-

<?php                                                  
$cfg['Servers'][$i]['controluser']   = 'username1';         
                                                    
$cfg['Servers'][$i]['controlpass']   = 'password1';         
                                                    
$cfg['Servers'][$i]['auth_type']     = 'config';
$cfg['Servers'][$i]['user']          = 'username2';      
$cfg['Servers'][$i]['password']      = 'password2';

?>

I managed to get into phpmyadmin, but get the message:

[COLOR="Red"]Invalid server index: ""[/COLOR] 

so obviously I need to do something else.

Can I just copy the config.inc.php from my windows system in its entirety, or are there any changes I need to make to get it to run under Ubuntu? I've looked in the documentation, but I can't find any reference to this.

---

### Post by DoctorBeaver on 2008-08-18
This is going frm bad to worse.

I found out that the default values are in config.default.php so I looked in there. The default username & password were what I though they were in the first place. Don't ask me why it didn't work.

Anyway, I deleted the contents of config.inc.php thinking that would be the end of the problem. Uh-uh. Now I get these error messages:

Warning: Cannot modify header information - headers already sent by (output started at /var/lib/phpmyadmin/config.inc.php:2) in /usr/share/phpmyadmin/libraries/core.lib.php on line 605

#0  PMA_sendHeaderLocation([http://localhost/phpmyadmin/index.php?lang=en-utf-8&token=b880656ccd2399261d499c84d7446f2a](http://localhost/phpmyadmin/index.php?lang=en-utf-8&token=b880656ccd2399261d499c84d7446f2a)) called at [/usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php:543]
#1  PMA_auth_set_user() called at [/usr/share/phpmyadmin/libraries/common.inc.php:758]
#2  require_once(/usr/share/phpmyadmin/libraries/common.inc.php) called at [/usr/share/phpmyadmin/index.php:34]


Fatal error: PMA_sendHeaderLocation called when headers are already sent! in /usr/share/phpmyadmin/libraries/common.lib.php on line 655

I have made no alterations to any files except for config.inc.php which is now once again empty.

HEEEEEEELLLLLLP! :(

---

### Post by ilovelinux33467 on 2008-08-18
Try Reinstalling Phpmyadmin

Remove it:
```
sudo apt-get remove phpmyadmin
```

Then Install it again:
```
sudo apt-get install phpmyadmin
```

Then, just to be sure:
```
sudo dpkg-reconfigure phpmyadmin
```

---

### Post by DoctorBeaver on 2008-08-18
I was thinking I may have to do that. Thanks for your help. It's much appreciated.

---

### Post by DoctorBeaver on 2008-08-19
ilovelinux33467 - I did the uninstall & get, but which webserver do I select? Ubuntu isn't on the list. It's got:

apache2
apache
apache-ssl
apashe-perl
lighttpd

---

### Post by DoctorBeaver on 2008-09-16
Cariboo - I've installed phpmyadmin using Synaptic, but when I point my browser at localhost/phpmyadmin I get a 404 error. What have I not done?

---

