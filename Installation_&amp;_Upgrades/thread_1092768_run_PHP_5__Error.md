---
title: "run PHP 5  Error"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by enrique786 on 2009-03-10
I have installed php from apt-get 

 after that i restart service of apache2 
$ sudo /etc/init.d/apache2 restart

 /etc/init.d/apache2 restart
 * Restarting web server apache2                                                           apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

then i open mozilla and write the this line on address bar

[http://127.0.1.1/Hi.php](http://127.0.1.1/Hi.php)

then enter  i got this  message

[FONT="Georgia"][SIZE="4"][COLOR="DarkGreen"]Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/Hi.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0[/COLOR][/SIZE][/FONT]



please help me

---

