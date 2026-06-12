---
title: "Apache2 no permission"
date: 2008-11-07
forum: General Help
---

### Post by Nitewalker on 2008-11-07
I have installed Apache2 from the package manager and when I try and access 127.0.0.1 it tells me I do not have permission to view?  I have updated the /etc/apache2/site-enabled directory and put in my own "xxx.xxx" file and I get the same result when I try and access the local host?  

nitewalker@smj:~$ cd /etc/apache2
nitewalker@smj:/etc/apache2$ ls -l
total 40
-rw-r--r-- 1 root root 10587 2008-06-25 07:49 apache2.conf
drwxr-xr-x 2 root root  4096 2008-11-06 22:38 conf.d
-rw-r--r-- 1 root root   378 2008-06-25 07:49 envvars
-rw-r--r-- 1 root root     0 2008-11-06 22:38 httpd.conf
drwxr-xr-x 2 root root  4096 2008-11-06 22:38 mods-available
drwxr-xr-x 2 root root  4096 2008-11-06 22:38 mods-enabled
-rw-r--r-- 1 root root    59 2008-06-25 07:49 ports.conf
drwxr-xr-x 2 root root  4096 2008-11-06 22:38 sites-available
drwxr-xr-x 2 root root  4096 2008-11-07 10:47 sites-enabled
nitewalker@smj:/etc/apache2$

---

### Post by Coreigh on 2008-11-07
What is the actual folder on the hard drive that the virtualhost in sites-enabled points to, and does the group www-data or your user have permission to that folder?

---

### Post by Nitewalker on 2008-11-07
Not sure what you are asking, I am fairly new to this, this is a copy of my file in sites-enabled. the directory & files in /var/www have owner & group full access and write, and other's = access.  When I enter [http://127.0.0.1/smj2.net](http://127.0.0.1/smj2.net) in web browser I get following: "You don't have permission to access /smj2.net/index.htm on this server."

NameVirtualHost *
<VirtualHost *>
	ServerAdmin [email]smj41@centurytel.net[/email]
	ServerName smj2.net
	Server Alias [www.smj2.net](www.smj2.net)
	DocumentRoot /var/www/smj2.net
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

### Post by Coreigh on 2008-11-07
When you go to [http://127.0.0.1/](http://127.0.0.1/) (or [http://localhost/](http://localhost/)) on the computer that apache is on you should see "It works!" that is the default page when you first install apache. You typed in [http://127.0.0.1/smj2.net](http://127.0.0.1/smj2.net). That is asking apache to show you what is on the folder called smj2.net. That is not what you want.

First see the line in the sites-enabled that says /var/www ? that is the folder on the computer where apache is installed, that by default, holds your web pages. If you created a webpage called smj2.net put it in that folder, but you also have to change the name, apache does not know what a .net page is. It is easiest to name it .htm or .html. There are many others but those are the two most basic.

So again from what you typed in [http://127.0.0.1/smj2.net](http://127.0.0.1/smj2.net) if smj2.net is a web page then rename it smj2.net.html or smj2.html and put it in the folder /var/www on the apache computer.

Here the Webmonkey site can explain this much better than I can. Start with the link below, but explore that site. It is a gold-mine for web site beginners.

[http://www.webmonkey.com/tutorial/Apache_for_Beginners]("http://www.webmonkey.com/tutorial/Apache_for_Beginners")

---

### Post by Nitewalker on 2008-11-07
Thanks a bunch for your help, I will check the site out:popcorn:

---

