---
title: "LAMP - how to run"
date: 2008-11-14
forum: General Help
---

### Post by kingleviathan on 2008-11-14
Hi Guys

I have installed LAMP using Tasksel on my 7.04 Ubuntu version.

It looks like it installed ok, after it installed it returned back to the console.

What do I do now? was a menu of options meant to pop up in the tasksel? or is there a command i am supposed to type in to get PHP or MySQL running?

Thanks

---

### Post by tvtech on 2008-11-14
it should be running and you should have access to them, as long as you set your passwords for mysql on install you should be all set.

---

### Post by tvtech on 2008-11-14
if you want an example of sql server and how it runs and you have a desktop install install it on the desktop / laptop by desktop install I mean x session with window manager. and install Amarok and set up your music data base via sql then move the database around. there are some pretty good tuts on Amaroks website for how to do all of this.

this way you can see it in a gui application, and then transfer the knowledge base the the command line server applications. That might help you out a bit!

---

### Post by kingleviathan on 2008-11-15
Ok..For some reason when I did tasksel...I was never asked to creat a password for MySQL.

So im following this instruction
sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables &
mysql -u root mysql
and
UPDATE user SET Password=PASSWORD('YOURNEWPASSWORD') WHERE User='root'; FLUSH PRIVILEGES; exit;

But I get this message?
ERROR 1290 (HY000): The MySQL server is running with the --skip-grant-tables option so it cannot execute this statement


What does this mean? and how can i create a password?

---

### Post by Ryadt on 2008-11-15
Ubuntu 7.04 is not supported anymore. So bugs can be expected.

---

