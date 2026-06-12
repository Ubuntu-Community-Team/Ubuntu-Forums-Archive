---
title: "[SOLVED] Setting up MySQL"
date: 2008-07-28
forum: General Help
---

### Post by ceclauson on 2008-07-28
Hello!

I'm trying to get a MySQL server working on my machine so that it can be accessed by scripts running on Apache.  However, I'm not sure how to get the server running with an account set up.  When I try to enter the shell by typing "mysql" at the prompt, I get the message:
```

ERROR 1045 (28000): Access denied for user 'ceclauson'@'localhost' (using password: NO)

```

When I try the command "mysql -h localhost -p -u root" (which my book says to do), it prompts for a password, but I'm not able to supply a password that works.

It seemed to me that I probably need to set up an account first, but I'm not sure how to do this.  I can disable MySQL under System > Administration > Services and start it up again by issuing "sudo mysqld" from the command line, but I still can't log on.

I'm unsure where to go from here.  If anyone has any advice, I'd be very appreciative.  Also, if anyone can recommend any good internet resources or books, that would be great, too.  (I've found that most of them tend to assume that you already have the system up and running, and have a username and password)

Thanks so much,
Cooper

---

### Post by mcduck on 2008-07-28
I'd recommend installing phpmyadmin, and then using that (through your web browser) to configure MySQL.

---

### Post by GreenN00b on 2008-07-28
The default user for mysql is root, you should lookup the syntax of the command line to see how to specify an user.
Also the mysql root password was requested at install, you should use that, but in case you forget it you can reset it this way:
```
mysqladmin -u root password <new_pass>
```

---

### Post by p_quarles on 2008-07-28
The "-p" option in the command you typed prompts you for password authentication, which won't work correctly until a password is actually set. First, you can open a MySQL root shell:
```
mysql -u root
```
To set the password:
```
set password for root@localhost = password('*new_root_passwd*');
```
Replace "new_root_passwd" with the actual password you want, leaving everything else verbatim. 

If you've already set the root password by accident, you'll also need to un-set it. I can't remember how to do that, but I know I found the trick easily on Google when I needed it (EDIT: and GreenN00b already posted it by the time I wrote this)

---

### Post by cariboo on 2008-07-28
If you setup Mysql server 5 from the repositories you have been prompted to enter a password for root. then you can use:

```
mysql -u root -p
```

as the others have said to access the mysql console. I hate using root to run any program so I usually set up another user right away to do this once you are in the console:

```
mysql> grant all privileges on *.* to <user>@localhost
    -> identified by '<password>' with grant option;
Query OK, 0 rows affected (0.00 sec)

mysql> grant all privileges on *.* to <user>@'%'
    -> identified by '<password>' with grant option;
Query OK, 0 rows affected (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql>
```

Of course replace <user> with your user name and <password> with oyur password.

Jim

---

### Post by ceclauson on 2008-07-28
Thanks so much for all your replies!

I got MySQL from the repositories, but it never prompted me for a password.  I wasn't able to use your guys' suggestions regarding logging in from root, because in each case it required a password that I didn't have.  However, as p_quarles suggested, I found the procedure online for changing the root password, and it worked.  I can now log on as root.

Here's the link to the site:
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)

Thanks again for your help,
Cooper

---

