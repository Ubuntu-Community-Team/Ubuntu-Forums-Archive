---
title: "Loading a .PHP file in firefox"
date: 2008-09-28
forum: General Help
---

### Post by smokeyjoe03 on 2008-09-28
Hi 1st post in these forums, just moved over to ubuntu from Win XP and I can already see all of the advantages. I'm trying to learn a bit of PHP for uni but i'm having troubles.

I have a .php file saved in my home folder, I tried to open it in Firefox (ver 3.0.3) but it asked whether I wanted to open it with a certain program or save it to my computer. Weird cos normally it just opens as a web page and displays whatever I tell it to using the echo command.

In the end I chose to open it in Firefox when prompted but nothing happened, now when I try to open the file in firefox from my home folder I get the following message: "could not be opened, because the associated helper application does not exist. Change the association in your preferences."

Whats going on? Anybody got any ideas?
TIA
smokeyjoe03

---

### Post by kenois on 2008-09-28
Php is a serverside scripting language, thus you must install a webserver with a php module to process your php file correctly.

It is common to use apache2 and the php module it provides. Install by issuing this command in a terminal:

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

(I also put in the mysql packages as these are commonly used by php, feel free to leave them out if they are not necessary for you).

Once you are done installing apache2, simply put your php file in /var/www/somedir

More comprehensive information can be found here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by smokeyjoe03 on 2008-09-28
......I havn't installed apache [insert red face]
Lol wish i'd never asked, feel silly.

Cheers kenois, probably would never have seen it if you hadn't pointed it out.

---

### Post by smokeyjoe03 on 2008-09-28
I'm still getting that:

/var/www/100.php could not be opened, because the associated helper application does not exist. Change the association in your preferences.

error message when trying to open any php file in Firefox. I've done a few searches and found it something to do with the application not being where I said it is. I tryed to cure it by clicking open with >> Firefox but still the same error, any ideas?

It says to check firefox's options and settings and click the applications tab and see what action the filetype is set to. However there is no option for a .PHP filetype.

---

### Post by kenois on 2008-09-28
Make sure apache is running by executing this command:

sudo /etc/init.d/apache2 start


then in firefox, point your browser to [http://localhost/100.php](http://localhost/100.php)

---

### Post by smokeyjoe03 on 2008-09-28
Nope, I get the same message.

I have figured it is a Firefox Problem, not a php problem. Firefox doesn't understand the .php filetype for some reason, like its lost a setting and there is no option to change it back.

---

### Post by mb_webguy on 2008-09-28
Is the php file in your /var/www directory?  That's Apache's default document root for web pages.  If the php file is somewhere else, Apache won't know to open it.

---

### Post by smokeyjoe03 on 2008-09-30
Yeah its in the /var/www/ directory. I have apache 2 installed. I have php5 installed.

The issue seems to be with firefox, it doesn't know what to do with .php files. I have tried uninstalling it and reinstalling it but no luck.

---

