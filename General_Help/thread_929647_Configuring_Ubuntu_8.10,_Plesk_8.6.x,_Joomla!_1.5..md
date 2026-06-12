---
title: "Configuring Ubuntu 8.10, Plesk 8.6.x, Joomla! 1.5.x and suPHP"
date: 2008-09-25
forum: General Help
---

### Post by DirtyMonkey on 2008-09-25
I had been struggling to understand how to set-up my Installations of Joomla! with the perfect file/folder permissions and had read previous threads and nothing seemed to work... but I think I've cracked it so wanted to post my findings because I'm sure others must be trying to figure this out and to confirm I have done it correctly... ;)

***NB: Replace anything in [] with your own settings.***

Set the correct file and folder permission settings via. SSH (If someone can actually explain in simple terms what this does...)

```
cd /var/www/vhosts/[yourdomain.com]
chown -R [yourdomain]:www-data httpdocs
chmod -R g+w httpdocs
find httpdocs -type d -exec chmod g+s {} \;
```

Then you need to create a php.ini and upload it to /httpdocs
I used the excellent PLESK Power Toys 4.3.0 to create mine:

```
# PHP version detected 5
<IfModule mod_suphp.c>
<Directory "/var/www/vhosts/[yourdomain.com]/httpdocs/">
php_admin_flag engine on
suPHP_Engine On
suPHP_ConfigPath "/var/www/vhosts/[yourdomain.com]/httpdocs/"
AddHandler php5-script .php
AddHandler x-httpd-php .php5
suPHP_AddHandler php5-script .php
<Files php.ini>
order allow,deny
deny from all
</Files>
php_value open_basedir "/tmp/"
php_value upload_tmp_dir "/var/www/vhosts/[yourdomain.com]/httpdocs/tmp/"
</Directory>
</IfModule>
```

I then restarted the Apache service via. Plesk Control Panel and I can FTP anywhere in /httpdocs and Joomla! is happy to write to cache etc...

Can anyone confirm that this set-up is secure?

Cheers, DM.

---

