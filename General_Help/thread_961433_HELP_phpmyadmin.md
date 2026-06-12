---
title: "HELP: phpmyadmin"
date: 2008-10-28
forum: General Help
---

### Post by xtremer on 2008-10-28
[B]hello guys

i've just installed phpmyadmin but i dunno how to access it, i tried localhost/phpmyadmin its not working, the www folder is working right.
also i searched for phpmyadmin folder in the whole harddisk folder by folder.
the synaptec manager tells me it is installed....but i cant find and put it on

plz i need  a solution ASAP.[/B]

---

### Post by ianhaycox on 2008-10-28
On my system /etc/apache2/conf.d/phpmyadmin.conf says it's all in /usr/share/phpmyadmin

Also do you have PHP working in Apache. A small test file in /var/www will help. E.g. phpinfo.php

```

<?php
phpinfo();

?>

```

---

### Post by Nepherte on 2008-10-28
This command will list where phpmyadmin is installed:
```
dpkg -L phpmyadmin
```

I believe it's either under /var/www/phpmyadmin or /usr/share/phpmyadmin. Since you didn't see it when examining whether the www folder works, it's located in the latter one.

---

### Post by xtremer on 2008-10-28
the php working fine wid me, but when i restarted the apache it gives me this msg:
Restarting web server apache2                                                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

---

### Post by Nepherte on 2008-10-28
You may ignore that message. That's why I did and never had any issues with running Apache locally.

---

### Post by xtremer on 2008-10-29
10x guys i found it by writing this in the browser : file:///usr/share/phpmyadmin/

lol but the wierdest thing if i browse the folders i cant find the folder phpmyadmin :)

---

### Post by ianhaycox on 2008-10-29
Looks like it might have installed OK. But for it to work you need to run it via Apache.

Do you have the following file ? :-

```

$ cat /etc/apache2/conf.d/phpmyadmin.conf

# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
	Options Indexes FollowSymLinks
	DirectoryIndex index.php

	# Authorize for setup
	<Files setup.php>
	    # For Apache 1.3 and 2.0
	    <IfModule mod_auth.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    # For Apache 2.2
	    <IfModule mod_authn_file.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    Require valid-user
	</Files>
	<IfModule mod_php4.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
</Directory>


```

---

