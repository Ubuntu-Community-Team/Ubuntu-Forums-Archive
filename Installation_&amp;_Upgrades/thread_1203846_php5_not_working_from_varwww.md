---
title: "php5 not working from /var/www"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by apextrooper1 on 2009-07-03
[FONT=Tahoma][SIZE=3]I completed a new install of server 9.04 and checked the LAMP package during the install script.

After install, browse to [FONT=Courier New][SIZE=2]http://myhost[/SIZE][/FONT] from another machine on my network and the "It Works!" page appears for both IE and FX.

Looks great but then change [FONT=Courier New][SIZE=2]/var/www/index.html[/SIZE][/FONT] to:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Start
[/SIZE][/FONT]      [FONT=Courier New][SIZE=2]<?php phpinfo(); ?>[/SIZE][/FONT]
  [FONT=Courier New][SIZE=2]End[/SIZE][/FONT]
  
  [FONT=Tahoma][SIZE=3]The browsers display[/SIZE][/FONT]
  [FONT=Courier New][SIZE=2]Start End[/SIZE][/FONT]

[FONT=Tahoma][SIZE=3]Strange but[/SIZE][/FONT][FONT=Courier New][SIZE=2] sudo a2enmod php5[/SIZE][/FONT]   [FONT=Tahoma][SIZE=3]reports already running but[/SIZE][/FONT] [FONT=Tahoma][SIZE=3]the php5 package was not installed so:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]sudo apt-get install php5[/SIZE][/FONT]

[FONT=Tahoma][SIZE=3]Changed owner:group  of [FONT=Courier New][SIZE=2]/var/www [/SIZE][/FONT] and files in it to www-data:www-data (previously root:root)

[/SIZE][/FONT]    [FONT=Tahoma][SIZE=3] The same failed result reported by he browsers.[/SIZE][/FONT]

   [FONT=Tahoma][SIZE=3]Next  [/SIZE][/FONT][FONT=Courier New][SIZE=2]sudo apt-get install phpmyadmin[/SIZE][/FONT]
   
  [FONT=Tahoma][SIZE=3]Browisng to:[/SIZE][/FONT] [http://myhost/phpmyadmin](http://myhost/phpmyadmin)
  [FONT=Tahoma][SIZE=3]Works properly.[/SIZE][/FONT]
   
  [FONT=Tahoma][SIZE=3]I think that this result shows php5 is installed and operating correctly, but not for the default path[/SIZE][/FONT] [FONT=Courier New][SIZE=2]/var/www[/SIZE][/FONT].

[FONT=Tahoma][SIZE=3]I think I'm having fun but I'm stuck! Is there a configuration guide or tutorial that can help me work through this problem?   Thanks in advance!
[/SIZE][/FONT][FONT=Tahoma][SIZE=3]
[/SIZE][/FONT]

---

### Post by jenkinbr on 2009-07-04
> **apextrooper1 said:**
> [FONT=Tahoma][SIZE=3]I completed a new install of server 9.04 and checked the LAMP package during the install script.

After install, browse to [FONT=Courier New][SIZE=2]http://myhost[/SIZE][/FONT] from another machine on my network and the "It Works!" page appears for both IE and FX.

Looks great but then change [FONT=Courier New][SIZE=2]/var/www/index.html[/SIZE][/FONT] to:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Start
[/SIZE][/FONT]      [FONT=Courier New][SIZE=2]<?php phpinfo(); ?>[/SIZE][/FONT]
  [FONT=Courier New][SIZE=2]End[/SIZE][/FONT]
  
  [FONT=Tahoma][SIZE=3]The browsers display[/SIZE][/FONT]
  [FONT=Courier New][SIZE=2]Start End[/SIZE][/FONT]

[FONT=Tahoma][SIZE=3]Strange but[/SIZE][/FONT][FONT=Courier New][SIZE=2] sudo a2enmod php5[/SIZE][/FONT]   [FONT=Tahoma][SIZE=3]reports already running but[/SIZE][/FONT] [FONT=Tahoma][SIZE=3]the php5 package was not installed so:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]sudo apt-get install php5[/SIZE][/FONT]

[FONT=Tahoma][SIZE=3]Changed owner:group  of [FONT=Courier New][SIZE=2]/var/www [/SIZE][/FONT] and files in it to www-data:www-data (previously root:root)

[/SIZE][/FONT]    [FONT=Tahoma][SIZE=3] The same failed result reported by he browsers.[/SIZE][/FONT]

   [FONT=Tahoma][SIZE=3]Next  [/SIZE][/FONT][FONT=Courier New][SIZE=2]sudo apt-get install phpmyadmin[/SIZE][/FONT]
   
  [FONT=Tahoma][SIZE=3]Browisng to:[/SIZE][/FONT] [http://myhost/phpmyadmin](http://myhost/phpmyadmin)
  [FONT=Tahoma][SIZE=3]Works properly.[/SIZE][/FONT]
   
  [FONT=Tahoma][SIZE=3]I think that this result shows php5 is installed and operating correctly, but not for the default path[/SIZE][/FONT] [FONT=Courier New][SIZE=2]/var/www[/SIZE][/FONT].

[FONT=Tahoma][SIZE=3]I think I'm having fun but I'm stuck! Is there a configuration guide or tutorial that can help me work through this problem?   Thanks in advance!
[/SIZE][/FONT][FONT=Tahoma][SIZE=3]
[/SIZE][/FONT]

Create a file in your /var/www folder called 'phpinfo.php'

Past in the following code;

[php]<?php phpinfo(); ?>
[/php]

I think your problem before is that the file contained ```
Start
<?php phpinfo(); ?>
End
``` and the PHP parser didn't read it properly, if at all.

Hope this helps.

---

### Post by apextrooper1 on 2009-07-04
> **jenkinbr said:**
> Create a file in your /var/www folder called 'phpinfo.php'

Past in the following code;

[php]<?php phpinfo(); ?>
[/php]

Thank you for this hint.  When the file phpinfo.php is created as above, it still does not work. However if I browse to [http://myhost/phpinfo.php](http://myhost/phpinfo.php) the php code runs properly.

If I add the following line to the end of /etc/apache2/apache2.conf:
AddHandler application/ x-httpd-php php html

Then the original file works properly.  The way I understand it, this directive in the apache2.conf will be applied to **all** pages hosted by this server.

In an attempt to localize the change to **only** the page in the /var/www path, I created /var/www/.htaccess with the following line:
AddHandler application/x-httpd-php .php .htm .html

This approach is still without success. I found a post [http://forums.digitalpoint.com/showthread.php?t=7584](http://forums.digitalpoint.com/showthread.php?t=7584) and tried a variety of combinations, and no joy.

I think the problems is that the Apache  AllowOverride directive defaults to None, which causes it to ignore the .htaccess files.  I've played with the adding AllowOverride to apache2.conf but location in the file is important and the apache2 docs are unclear about this syntax. Still working this one.

Having fun now!!

---

