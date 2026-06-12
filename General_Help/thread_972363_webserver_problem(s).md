---
title: "webserver problem(s)"
date: 2008-11-05
forum: General Help
---

### Post by cje on 2008-11-05
I've been running an ubuntu test server with apache2

The server has been located at my LAN network (192.168.0.x). There has been no problems. 

Today I moved the server to another LAN network (192.168.10.x). 

After moving it I've got some problems;
1) I'm not able to brows my webfolders at LAN 10.x from LAN 0.x (page loading error)
I may ping the server from LAN 0.x and there is no problem accessing my VNC server.
2) and, if I move over to the webserver and try accessing localhost I get the following message: 
"The server encountered an internal error or misconfiguration and was unable to complete your request."

I've been searching the forum w/o any success. 

Thanks for any suggestions!!

---

### Post by cje on 2008-11-07
... anyone with any ideas?

---

### Post by ju2wheels on 2008-11-07
When you configured apache did you setup to specifically bind to its old ip address?

Can you post the contents of /etc/apache2/ports.conf and /etc/apache2/sites-enabled/000-default if you dont mind.

---

### Post by cje on 2008-11-08
Thanks for replying

Ports:
--------------------------------------------------
Listen 80
Listen 8080
Listen 20
Listen 21

<IfModule mod_ssl.c>
    Listen 443
</IfModule>
--------------------------------------------------

000-default:
--------------------------------------------------
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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
--------------------------------------------------

I do also include hosts file:
--------------------------------------------------
127.0.0.1 localhost
192.168.10.20 webserver

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
255.255.255.0 subnet mask
192.168.10.1 gateway
--------------------------------------------------

Pls do also note; 
when I had the webserver at the 0.x LAN I could connect to the VNC server using the web server name. After moving the webserver to 10.x LAN I'm only able to connect using the IP.

Thanks for any suggestions.

---

### Post by Iowan on 2008-11-08
I presume if you can ping between 0.X and 10.X, you have a router (or two) set up to "connect" between the two networks?

---

### Post by cje on 2008-11-08
.... seems like the problem is related to wordpress. maybe I have to change forum ;-)

thanks anyway for your time

---

