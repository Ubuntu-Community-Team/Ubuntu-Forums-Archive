---
title: "How to:  Move the MySQL data directory in *buntu"
date: 2008-08-22
forum: General Help
---

### Post by mb_webguy on 2008-08-22
I've been struggling with this for a while, and finally discovered the (frustratingly simple) solution to the problem of moving the default MySQL data directory.  Since none of the many tutorials I found online mentioned it, I thought I'd share.

[LIST=1]
[*]Open the terminal
[*]Stop MySQL with the command "sudo /etc/init.d/mysql stop".
[*]Copy the existing data directory (by default located in /var/lib/mysql) using the command "sudo cp -R -p /var/lib/mysql /path/to/new/datadir".  All you need are the data files, so delete the others with the command "sudo rm /path/to/new/datadir".  (You will get a message about not being able to delete some directories, but that's what you want.)
[*]Edit the MySQL configuration file with the command "gksu gedit /etc/mysql/my.cnf".  Find the entry for "datadir", and change the path (which should be "/var/lib/mysql") to the new data directory.
[*]NOW FOR THE PART THE OTHER TUTORIALS DON'T MENTION...  From 7.10 (Gutsy Gibbon) forward, Ubuntu uses some security software called AppArmor that specifies the areas of your filesystem applications are allowed to access.  Unless you modify the AppArmor profile for MySQL, you'll never be able to restart MySQL with the new datadir location.  [LIST]
[*]In the terminal, enter the command "sudo gedit /etc/apparmor.d/usr.sbin.mysqld". 
[*]Copy the lines beginning with "/var/lib/mysql", comment out the originals with hash marks ("#"), and paste the lines below the originals.
[*]Now change "/var/lib/mysql" in the two new lines with "/path/to/new/datadir".  Save and close the file.
[*]Reload the AppArmor profiles with the command "sudo /etc/init.d/apparmor reload".
[/LIST]
[*]Restart MySQL with the command "sudo /etc/init.d/mysql restart".  With any luck, MySQL will start with no errors, and your data will be stored in the new location!
[/LIST]

---

### Post by taecha on 2008-08-27
Great how-to mb_webguy. Thank you.

I have tried numerous other tutorials which all did not work. Your changing the AppArmor profile seems to be the key. However, I had to reboot my machine in order to get access to the new directory since without a reboot the old error message kept appearing.

Thanks again. You saved my day!

---

### Post by mb_webguy on 2008-08-27
Does the mysql user have full permissions on the datadir and all subdirectories?

---

### Post by brianslattery on 2008-10-27
This is amazing. I have been searching/chmodding/etc for hours, all because nobody else wrote about apparmor. Thank you so much.

---

### Post by crom.osec on 2008-11-13
Thank you, your article helped me to solve mysql relocation problem.

---

### Post by guyfromfl on 2011-10-19
Thank you for this!

Just want to confirm this fixes on 11.10 also...I'm now fully restored and happily an ubuntu user again!

Thanks again

---

### Post by gshreya3 on 2012-02-07
I am new to linux
I have followed the same steps mentioned. But after restarting mysql service, when I login or want to connect database. It is showing me following error.

ERROR 2002 (HY000): Can't connect to local MySQL server through socket  '/var/run/mysqld/mysqld.sock' (2)

I am using Ubuntu 10.4 LTS - 64-bit. And Mysql database version is 5.1.41.
Kindly help...

---

