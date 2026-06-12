---
title: "Step by Step setup for OWA SSL Reverse proxy using apache"
date: 2008-08-04
forum: General Help
---

### Post by bbaglin on 2008-08-04
Hi Guys & Gals&#8230;
 
Well this is my second take on sharing this info&#8230; I almost wasn&#8217;t going to after typing it all out and accident clicking something on my laptop&#8217;s touchpad. Anyway here goes.
 
I came across a scenario where I needed to provide access to OWA to the outside network. I had a number if IP available to me but I wasn&#8217;t to keen on the idea of exposing my Exchange server to the internet (especially when I had a DMZ to use) 
 
I decided to setup an Apache SSL reverse proxy. I found a lot of information about how to set it up but none of the documentation was ever quite complete. So I thought I&#8217;d share my experience to possibly help other out there. 
 
Now I actually ended up using Debian&#8217;s Netinstall to keep the system to a minimum (I like things to be nice and clean&#8230; it saves time when trying to work out why something is not working) and I also wanted all my config in the httpd.conf file so it was in theory easy to edit/share. This method will work for both Debain and Ubuntu (Server and Desktop)
 
The overall rundown on my procedures was in the following order
Install Linux
Install SSH
Install Apache2
Install OpenSSL
Set Date/Time
Create Digital Cert
Setup Apache
restart everything
test&#8230;
 
**Installing Linux**
If you&#8217;re already in here then I think you should already know how to install&#8230; but just run through a basic install. Im going to run through the installation of the packages we need anyway. If you install LAMP you get to skip the install apache part.
Before starting I&#8217;d recommend you update all your packages to latest versions
 
*sudo apt-get update*
*sudo apt-get upgrade*
 
**Installing SSH**For those of you who don&#8217;t know SSH will give you remote access to the server command line. Kind of like a secure version of telnet. PuTTY is a great Windows too for connecting to SSH servers&#8230; google it
Also SSH uses port 22 if you need to make any firewall changes.
To install SSH just type the following:
 
*sudo apt-get install SSH*
 
**Installing Apache2**
So after installing SSH you can now sit back at your desk and not have to worry about standing in that Datacentre (or cold comms room). Assuming you haven&#8217;t installed Apache with a LAMP installation type in the following:
 
*sudo apt-get install apache2*
 
**Installing OpenSSL**OpenSSL we are using to create self-signed digital certificates. If you already have your own certificates you don&#8217;t really need this. To install OpenSSL type the following
 
*sudo apt-get install openssl*
 
***Note: you can install all of these packages in one go if you like using the following command***
 
*sudo apt-get install ssh apache2 openssl*
 
Before we start the first step of creating a digital certificate Im going to ask that you check the date and time of your server. To check the date from cmd-line type:
*Date*
To set the time or Date try either of the following (depending on what you need to change. Note the time is 24hr)
*Date M/D/YYYY*
Or
*Date TT:MM *
 
**Creating a Digital Certificate**
Now there are plenty of ways to create a digital certificate but this is the way I created mine. First off I created a directory /etc/apache2/ssl then opened the directory to work from
 
*sudo mkdir /etc/apache2/ssl*
*cd /etc/apache2/ssl *
 
I then ran the following commands (taken from **[http://www.tc.umn.edu/~brams006/selfsign.html](http://www.tc.umn.edu/~brams006/selfsign.html)**)
 
*sudo openssl genrsa -des3 -out server.key 1024 *
*sudo openssl req -new -key server.key -out server.csr *
*sudo openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt*
 
This will create your digital certificate and also the security key for it. The main thing to watch for is the common name needs to match your FQDN (eg. remote.company.com) If it doesn&#8217;t you won&#8217;t be able trust the certificate properly.
 
The commands below will remove the passphrase from the certificate so you don&#8217;t need to type it each time you need to restart the server or apache2 service
 
*sudo openssl rsa -in server.key -out server.key.insecure*
*sudo mv server.key server.key.secure*
*sudo mv server.key.insecure server.key *
 
**Configuring Apache**
The config im going to post here is the same I used. And it seems to work fine (feel free to post working changes if you wish or any other comments). First off though open your httpd.conf file.
 
*sudo nano /etc/apache2/httpd.conf*
 
Paste this into your nano session (make sure you replace remote.company.com with your external web address and internal.local with your server names)
 
*LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so*
*LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so*
*LoadModule ssl_module /usr/lib/apache2/modules/mod_ssl.so*
*LoadModule proxy_connect_module /usr/lib/apache2/modules/mod_proxy_connect.so*
*LoadModule headers_module /usr/lib/apache2/modules/mod_headers.so*
*LoadModule cache_module /usr/lib/apache2/modules/mod_cache.so*
*LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so*
 
*listen 443*
 
*Servername remote.company.com*
*ServerAdmin [EMAIL="administrator@company.com"]administrator@company.com[/EMAIL]*
 
*NameVirtualHost remote.company.com:443*
*<VirtualHost remote.company.com:443>*
 
*RewriteEngine On*
*RequestHeader set Front-End-Https "On"*
*ProxyPreserveHost On*
*SSLEngine On*
*SSLCertificateFile /etc/apache2/ssl/server.crt*
*SSLCertificateKeyFile /etc/apache2/ssl/server.key*
 
*ProxyPass /exchange [http://exchangeserver/exchange](http://exchangeserver/exchange)*
*ProxyPassReverse /exchange [http://exchangeserver/exchange](http://exchangeserver/exchange)*
 
*ProxyPass /exchweb [http://exchangeserver/exchweb](http://exchangeserver/exchweb)*
*    ProxyPassReverse /exchweb [http://exchangeserver/exchweb](http://exchangeserver/exchweb)*
 
*ProxyPass /public [http://exchangeserver/public](http://exchangeserver/public)*
*    ProxyPassReverse /public [http://exchangeserver/public](http://exchangeserver/public)*
 
*ProxyPass / [http://localhost/](http://localhost/)*
*ProxyPassReverse / [http://localhost/](http://localhost/)*
 
*CacheDisable **
*</VirtualHost>*
Now save that config (ctrl + x) I also edited one line in the the default site&#8230;
 
*Sudo nano /etc/apache2/sites-available/default*
 
*#RedirectMatch ^/$ /apache2-default/*
 
This comment was to stop the default redirection to the apache test page (its about 16 lines down)
 
Now restart apache
 
*sudo /etc/init.d/apache2 restart*
 
and test. One thing I did to make the process easier was to have a forwarder on the main index.html
 
*Sudo nano /var/www/index.html*
 
Paste this into nano
 
*<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">*
*<html>*
*<head>*
*<title>Redirecting to https://remote.company.com/exchange</title>*
*<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">*
*</head>*
*<body>*
*<div align="center">*
*<p><font size="2" face="Arial, Helvetica, sans-serif">Redirecting to <a href="https://remote.company.com/exchange">https://remote.company.com/exchange</a </font></p>*
*<p> <font size="2" face="Arial, Helvetica, sans-serif">*
*<SCRIPT LANGUAGE="JavaScript">*
*window.location="https://remote.company.com/exchange";*
*</script>*
*</font> </p>*
*</div>*
*</body>*
*</html>*
 
Now this may not be an ideal setup for everyone but it worked well for this stand alone server&#8230; Feel free to make suggestions and changes. Or if anyone thinks of any security flaws.

---

### Post by pwyzorski on 2008-08-25
bbaglin,

  I was reviewing your article; "Step by Step setup for OWA SSL Reverse proxy using apache" and I had some questions.

  Is this OWA 2003 or 2007?


  Were you able to get EAS (Exchange ActiveSync) services working?

  How about OAB (Offline Address Book)?

  How about AutoDiscover?


Just curious....

---

### Post by ccreamer_22 on 2012-04-26
This is great! 4 years later and it is still more than relevant. One issue I had was when I restarted apache, I received the following error:

(98)Address already in use: make_sock: could not bind to address 0.0.0.0:443

So I ran the following command:

grep 443 /etc/apache2/*


/etc/apache2/httpd.conf:listen 443
/etc/apache2/httpd.conf:NameVirtualHost 66.11.7.2:443
/etc/apache2/httpd.conf:<VirtualHost 66.11.7.2:443>
/etc/apache2/ports.conf:    # If you add NameVirtualHost *:443 here, you will also have to change
/etc/apache2/ports.conf:    # to <VirtualHost *:443>
/etc/apache2/ports.conf:    Listen 443
/etc/apache2/ports.conf:    Listen 443

I went into ports.conf and commented out the modules and lines.

---

### Post by oldos2er on 2012-04-26
Closed.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

