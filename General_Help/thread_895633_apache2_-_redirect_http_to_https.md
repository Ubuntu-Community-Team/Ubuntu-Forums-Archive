---
title: "apache2 - redirect http to https"
date: 2008-08-20
forum: General Help
---

### Post by acidzfire on 2008-08-20
Ubuntu 7.10
Apache2

Ok so I have a couple of problems. I got a webserver with ssl. I can access the page fine entering https in the browser. When trying to access it using http i get an error that website is not found. What I want is for it to redirect anyone using http to https.
Here is my sites-enabled/000-default contents:
```

NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin webmaster@site.com
	DocumentRoot /var/www/
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

```

And here is my 000-ssl contents

```

NameVirtualHost *:443
<VirtualHost *:443>
	ServerAdmin webmaster@site.com 	
	DocumentRoot /var/www/
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
SSLEngine on
SSLCertificateFile /etc/apache2/ssl/server.crt
SSLCertificateKeyFile /etc/apache2/ssl/server.key

</VirtualHost>


```

I have tried putting this into the 000-default file under virtual host 
```
	
RewriteEngine on
RewriteCond   %{SERVER_PORT}  !^443$

```

I've also tried putting 
```

Redirect / https://foo.bar.com

```
 in as well.

The other thing I have tried is making a file called forcessl.conf and putting it into the /etc/apache2/conf.d/. directory which usually works for me with httpd in redhat. Its contents are:
```

<VirtualHost _default_:80>
RewriteEngine on
RewriteCond   %{SERVER_PORT}  !^443$
</VirtualHost>

```

None of them seem to work. I of course restart apache after every change, and get no errors, but no changes. I can still get in using https, get a page not found with http, and no redirection. Any ideas?

Thanks in advance.

---

### Post by nedmas on 2008-08-28
Hay i've just been doing a similar thing and here is the code i got to work.

```

RewriteEngine on
RewriteCond  %{HTTPS}  ^off$
RewriteRule  ^/foo/?(.*) https://example.com/foo/$1 [L,R]

```

Let me know if this helps or not.

---

### Post by acidzfire on 2008-08-28
Couldn't get this to work either.

---

### Post by nedmas on 2008-08-29
Have you enabled the rewrite module?

Also I realized that the example i gave you wasn't the best, try this instead:

```

RewriteEngine on
RewriteCond  %{HTTPS}  ^off$
RewriteCond  %{HTTP_HOST} (.*)
RewriteRule  ^(.*)/? https://%1/$1 [L,R]

```

So basically it checks if the request used HTTPS if it didn't then it reconstructs the request and sends it again but with HTTPS this time.

If this doesn't work post exactly what config you tried.

---

### Post by acidzfire on 2008-08-30
I tried this as well and could not get it to work. I think that the server is not responding to http at all from outside my network. When I try to go to the site using http i get a page not found, but https works fine. When inside my network, http will reroute to https as it should. Is it possible that when I created the self signed cert, and set up the server, I set it to deny http? 
At this point, this is what I have in my apache2.conf file that allows the redirect in the local network:
> <VirtualHost _default_:80>
RewriteEngine on
RewriteCond   %{SERVER_PORT}  !^443$
RewriteRule ^.*$ https://%{SERVER_NAME}%{REQUEST_URI} [L,R]
</VirtualHost>


---

### Post by datajelly on 2008-09-05
Since you have it setup so that there's two virtual hosts - one that listens on port 80 (HTTP), and one that listens on port 443 (HTTPS)... can't you just always redirect any requests to the port 80 host? There's no need to use the RewriteCond that checks the server port.

[http://blog.datajelly.com/2008/09/using-ssl-in-apache-for-certain-pages.html]("http://blog.datajelly.com/2008/09/using-ssl-in-apache-for-certain-pages.html")

```
<VirtualHost *:80>
  ServerName www.domain.com
  <Location />
    Redirect permanent / https://www.domain.com/
  </Location>
</VirtualHost>
<VirtualHost *:443>
  ServerName www.domain.com
  SSLEngine on
  SSLCipherSuite ALL:!ADH:! EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL
  SSLCertificateFile "C:/cert.pem"
  SSLCertificateKeyFile "C:/private.pem"
  BrowserMatch ".*MSIE.*" nokeepalive ssl-unclean-shutdown downgrade-1.0 force-response-1.0

... configuration goes here ...
</VirtualHost>
```

---

### Post by skabople on 2012-04-07
Look here is how it's done. Just redirect everything on port 80 to https. Here is how I did it:


[LIST]
[*]First we shall edit the /etc/apache2/apache2.conf file and change:
[/LIST]
         ```
# Include module configuration:
                    Include /etc/apache2/mods-enabled/*.load
                    Include /etc/apache2/mods-enabled/*.conf
```
[LIST]
[*]To this code instead
[/LIST]
[INDENT]```
# Include module configuration:
Include /etc/apache2/mods-available/*.load
Include /etc/apache2/mods-available/*.conf
```[/INDENT]Of course you can just enable the necessary modules for the next part but I was lazy lol


[LIST]
[*]Now in the /etc/apache2/httpd.conf file we will add this:
[/LIST]
[INDENT]```
<VirtualHost *:80>
  RewriteEngine On
  RewriteCond %{SERVER_PORT} ^80$
  RewriteRule .* https://%{SERVER_NAME}%{REQUEST_URI} [R,L]
</VirtualHost>
```[/INDENT]Sweet! Everything on port 80 is redirected to HTTPS! If this doesn't work then you've done something wrong...

Regards,
Kyle

---

### Post by oldos2er on 2012-04-07
Closed, necromancy.

---

