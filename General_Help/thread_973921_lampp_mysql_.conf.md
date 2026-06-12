---
title: "lampp mysql .conf?"
date: 2008-11-07
forum: General Help
---

### Post by gleble on 2008-11-07
Lampp's phpadmin won't let me in. Gives a mysql error invalid settings. How do I check my host, username and password for mysql running under lampp?

---

### Post by tiberiup on 2008-11-07
you can try :
lampp security         (in your lamp directory , the default is /opt/lampp/lampp security)

---

### Post by Nepherte on 2008-11-07
> **gleble said:**
> Lampp's phpadmin won't let me in. Gives a mysql error invalid settings. How do I check my host, username and password for mysql running under lampp?
You won't find the password and username of mysql in a configuration file, but in a mysql database itself. Which requires...a username and password.

A default mysql installation only has one user 'root' and without a password. It's possible lampp has already asked you to set a password for root, maybe not. Check out lampp security as mentioned above.

p.s the configuration file for mysql is my.cnf

---

### Post by gleble on 2008-11-07
When I check security I get the code below which contains the line
```
XAMPP: MySQL has a root passwort set. Fine! :)
```
Which is not fine. I still get the same error. Any other ideas.

```
[CODE]neil@neil-laptop:/opt/lampp$ sudo ./lampp security
XAMPP: Quick security check...
XAMPP: Your XAMPP pages are NOT secured by a password.
XAMPP: Do you want to set a password? [yes] n
XAMPP: MySQL is accessable via network.
XAMPP: Normaly that's not recommended. Do you want me to turn it off? [yes] y
XAMPP: Turned off.
XAMPP: Stopping MySQL...
XAMPP: Starting MySQL...
XAMPP: MySQL has a root passwort set. Fine! :)
XAMPP: The FTP password is still set to 'lampp'.
XAMPP: Do you want to change the password? [yes] y
XAMPP: Password: 
XAMPP: Password (again): 
XAMPP: Reload ProFTPD...
XAMPP: Done.
neil@neil-laptop:/opt/lampp$ 
```[/CODE]

---

### Post by gleble on 2008-11-07
This little script results in success, so the password is ***** but even if I make that the lampp password I still can't get into myphpadmin.

Any ideas


[PHP]<?php
$dbcnx = @mysql_connect('localhost', 'root', '*****');
if (!$dbcnx) {
echo( '<p>Unable to connect to the ' .
'database server at this time.</p>' );
exit();
}
else{
echo('Success');
}
?>[/PHP]

---

### Post by arajapandi on 2009-06-30
Open **/opt/lampp/phpmyadmin/libraries/dbi/mysql.dbi.lib.php** u can see the below code
[php] global $cfg;
 if (empty($client_flags)) {
  if ($cfg['PersistentConnections']) {
            $link = @mysql_pconnect($server, $user, $password);
        } else {
....etc
[/php]just change it to

[php] global $cfg;

$server = 'localhost';
$user= 'root';
$password= '*****';


if (empty($client_flags)) {
  if ($cfg['PersistentConnections']) {
            $link = @mysql_pconnect($server, $user, $password);
        } else {
....etc
[/php]> **gleble said:**
> This little script results in success, so the password is ***** but even if I make that the lampp password I still can't get into myphpadmin.

Any ideas


[php]<?php
$dbcnx = @mysql_connect('localhost', 'root', '*****');
if (!$dbcnx) {
echo( '<p>Unable to connect to the ' .
'database server at this time.</p>' );
exit();
}
else{
echo('Success');
}
?>[/php]

---

### Post by gleble on 2009-06-30
My situation has change but I still have the same problem. See
[http://ubuntuforums.org/showthread.php?t=1200611]("http://ubuntuforums.org/showthread.php?t=1200611")

---

