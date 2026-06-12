---
title: "Apache2 - Service Temporarily Unavailable"
date: 2008-09-12
forum: General Help
---

### Post by rugbert on 2008-09-12
it WAS working, but now it does not. not from a machine in the same subnet or from the local machine it self.
the server's host name is myserver.test.org

Here is my virtual host file 
```

<VirtualHost 10.1.10.24:80>
        ServerAdmin webmaster@localhost
        ServerName myserver.test.org
        ServerAlias www.myserver.test.org

        DocumentRoot /var/www/myserver.test.org/html


        <Directory />
                Options None
                AllowOverride None
        </Directory>

        <IfModule mod_deflate.c>
                <Location />
                        SetOutputFilter DEFLATE
                        BrowserMatch ^Mozilla/4 gzip-only-text/html
                        BrowserMatch ^Mozilla/4\.0[678] no-gzip
                        BrowserMatch \bMSI[E] !no-gzip !gzip-only-text/html
                        SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
                        Header append Vary User-Agent env=!dont-vary
                </Location>
        </IfModule>

        <Directory /var/www/myserver.test.org/html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        #SuexecUserGroup awstats nogroup

####### Webalizer redirection
        Alias /webalizer/ /var/www/myserver.test.org/webalizer/
<Directory "/var/www/myserver.test.org/webalizer">
AllowOverride All
</Directory>
        RewriteEngine on
        RewriteLog "/var/log/apache2/rewrite.log"
        RewriteLogLevel 0
#        AllowOverride None


        # Don't Rewrite static content into zope
        RewriteRule ^/webalizer - [L]

        # Use mod_proxy and Zope's VirtualHostMonster to serve Zope from behind Apache
#        RewriteRule ^/(.*) 

http://localhost:9673/VirtualHostBase/http/www.sample.com:80/site_main/VirtualHostRoot/$1 [P]



       Alias /awstats-icon/ /usr/share/awstats/icon/
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
                AuthType Basic
                AuthName "Speaker.gov CGI"
                AuthUserFile /etc/awstats/.htpasswd
                require valid-user
                BrowserMatch "MSIE" AuthDigestEnableQueryStringHack=On
        </Directory>

        ErrorLog /var/log/apache2/myserver.test.org-error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel notice

        CustomLog /var/log/apache2/myserver.test.org-access.log combined

        RewriteEngine On
        #RewriteLogLevel 4
        #RewriteLog "/var/log/apache2/rewrite.log"

        #From cissecurity.org
        RewriteRule [^a-zA-Z0-9|\.|/|_|-] - [F]
        RewriteCond %{REQUEST_METHOD} ^TRACE
        RewriteRule .* - [F]

        RewriteCond %{REQUEST_URI} 

\.(exe|com|dll|conf|log|htr|cer|cdx|bat|cmd|mdb|asp|aspx|zip|rar|cfg|dbf|udl|old|bak|c|php
)$
        RewriteRule ^(.*) http://%{HTTP_HOST}/$1 [F]

        #Also wanted .c ... but that filters out all .css files ... So I added it to the extension 

filter above
        RewriteCond %{REQUEST_URI} 

(/|\.)(\.\.|\./|\\|\:|\%|\&|\#|\<|\>|\$|\@|\!|\,|\~|\'|\;|passwd|_vti|backup|root|bak|bkup
|test|temp|etc|odbc|w3svc|_derived|netcat|password|nobody)(/|\.)
        RewriteCond %{REQUEST_URI} !/zroot
        RewriteRule ^(.*) http://%{HTTP_HOST}/$1 [F]

        RewriteCond %{QUERY_STRING} 

\.\.|\./|\\|\:|\%|\&|\#|\<|\>|\$|\@|\!|\,|\~|\'|\;|passwd|_vti|backup|root|bak|bkup|test|
temp|etc|odbc|w3svc|_derived|netcat|password|admin|nobody
        RewriteRule ^(.*) http://%{HTTP_HOST}/$1 [F]

        #/tools available to internal networks
        #/tools/**/files/* available to all
        RewriteCond %{REQUEST_URI} !^/tools/.*/files/.*
        RewriteCond %{REQUEST_URI} ^/tools
        RewriteCond %{REMOTE_ADDR} !137\.18\.\d{1,3}\.\d{1,3}
        RewriteCond %{REMOTE_ADDR} !143\.(228|231)\.\d{1,3}\.\d{1,3}
        RewriteRule ^(.*) http://%{HTTP_HOST}/$1 [F]

        #/tools redirect to https for internal networks
        #/tools/**/files* no redirect
        RewriteCond %{REQUEST_URI} !^/tools/.*/files/.*
        RewriteCond %{REQUEST_URI} ^/tools
        #RewriteCond %{REMOTE_ADDR} 137\.18\.\d{1,3}\.\d{1,3} [OR]
        #RewriteCond %{REMOTE_ADDR} 143\.(228|231)\.\d{1,3}\.\d{1,3}
        RewriteRule ^/(.*) https://%{HTTP_HOST}/$1 [L,R]

        #**/admin/** available to internal networks
        #**/admin/**/files/* available to all
        RewriteCond %{REQUEST_URI} !/admin/.*/files/.*
        RewriteCond %{REQUEST_URI} (/admin$|/admin/)
        RewriteCond %{REMOTE_ADDR} !137\.18\.\d{1,3}\.\d{1,3}
        RewriteCond %{REMOTE_ADDR} !143\.(228|231)\.\d{1,3}\.\d{1,3}
        RewriteRule ^(.*) http://%{HTTP_HOST}/$1 [F]

        #**/admin/** redirect to https for internal networks
        #**/admin/**/files/* no redirect
        RewriteCond %{REQUEST_URI} !/admin/.*/files/.*
        RewriteCond %{REQUEST_URI} (/admin$|/admin/)
        #RewriteCond %{REMOTE_ADDR} 137\.18\.\d{1,3}\.\d{1,3} [OR]
        #RewriteCond %{REMOTE_ADDR} 143\.(228|231)\.\d{1,3}\.\d{1,3}
        RewriteRule ^/(.*) https://%{HTTP_HOST}/$1 [L,R]

        #**/manage/** available to internal networks only
        #RewriteCond %{REQUEST_URI} 

/manage(_main|_menu|_workspace|_access|_UndoForm|_owner|_findForm|_top_frame)?($|/)
        RewriteCond %{REQUEST_URI} /manage(_.*)?($|/)
        RewriteCond %{REMOTE_ADDR} !137\.18\.\d{1,3}\.\d{1,3}
        RewriteCond %{REMOTE_ADDR} !143\.(228|231)\.\d{1,3}\.\d{1,3}
        RewriteRule ^(.*) http://%{HTTP_HOST}/$1 [F]

        #**/manage/** redirect to https for internal networks
        #RewriteCond %{REQUEST_URI} 

/manage(_main|_menu|_workspace|_access|_UndoForm|_owner|_findForm|_top_frame)?($|/)
        RewriteCond %{REQUEST_URI} /manage(_.*)?($|/)
        #RewriteCond %{REMOTE_ADDR} 137\.18\.\d{1,3}\.\d{1,3} [OR]
        #RewriteCond %{REMOTE_ADDR} 143\.(228|231)\.\d{1,3}\.\d{1,3}
        RewriteRule ^/(.*) https://%{HTTP_HOST}/$1 [L,R]

        #**/Control_Panel/** available to internal networks only
        RewriteCond %{REQUEST_URI} /Control_Panel($|/)
        RewriteCond %{REMOTE_ADDR} !137\.18\.\d{1,3}\.\d{1,3}
        RewriteCond %{REMOTE_ADDR} !143\.(228|231)\.\d{1,3}\.\d{1,3}
        RewriteRule ^(.*) http://%{HTTP_HOST}/$1 [F]

        #**/Control_Panel/** redirect to https for internal networks
        RewriteCond %{REQUEST_URI} /Control_Panel($|/)
        #RewriteCond %{REMOTE_ADDR} 137\.18\.\d{1,3}\.\d{1,3} [OR]
        #RewriteCond %{REMOTE_ADDR} 143\.(228|231)\.\d{1,3}\.\d{1,3}
        RewriteRule ^/(.*) https://%{HTTP_HOST}/$1 [L,R]

        RewriteCond %{REQUEST_URI} ^/zroot
        RewriteCond %{REMOTE_ADDR} !137\.18\.\d{1,3}\.\d{1,3}
        RewriteCond %{REMOTE_ADDR} !143\.(228|231)\.\d{1,3}\.\d{1,3}
        RewriteRule ^(.*) http://%{HTTP_HOST}/$1 [F]

        RewriteCond %{REQUEST_URI} ^/zroot
        RewriteRule ^(.*) https://%{HTTP_HOST}/$1 [L,R]

        RewriteCond %{REQUEST_URI} !^/blog
        RewriteCond %{REQUEST_URI} !^/cgi-bin
        RewriteCond %{REQUEST_URI} !^/awstats
        RewriteCond %{REQUEST_URI} !^/phpmyadmin
        RewriteRule ^/(.*) 

http://127.0.0.1:1080/VirtualHostBase/http/%{HTTP_HOST}:80/impactzones.com/VirtualHostRoot/$1 [L,P
]

</VirtualHost>

```

---

### Post by tekky on 2008-09-12
Well, the 503 error is based on that the config file has changed, so it's assuming you're making changes to it.  The easiest remedy would be sudo /etc/init.d/apache restart.  Which means you're done editing the file.  

Try this out and see if it helps.  If it doesn't please post any apache .log files you have.

---

### Post by rugbert on 2008-09-12
I restart after every change I make, and I usually unmake the changes too.

but heres what I get in the error log
```


[Fri Sep 12 08:24:47 2008] [notice] caught SIGTERM, shutting down
[Fri Sep 12 08:24:58 2008] [notice] ModSecurity for Apache 2.1.2 configured
[Fri Sep 12 08:24:59 2008] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c configured -- resuming normal operations

```
over and over

---

