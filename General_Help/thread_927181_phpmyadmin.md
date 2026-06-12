---
title: "phpmyadmin"
date: 2008-09-22
forum: General Help
---

### Post by lahp on 2008-09-22
hi i need to be able to put a password on my phpmyadmin any help on this and maybe more configs?

---

### Post by stickmangumby on 2008-09-22
I believe that you log in to your phpMyAdmin using your MySQL username and password. So you need to set one of them.

Is phpMyAdmin prompting you for a username/password? Or can you just enter root as the username and nothing as the password?

To set a root password, enter the following at the Terminal:

```

mysqladmin -u root password ThisIsThePasswordThatIWantToUse!!

```

---

### Post by lahp on 2008-09-22
ye just eneter my user and no pass ... but it says i need to be a super user (sudo no work)

---

### Post by stickmangumby on 2008-09-22
Oh, are you on a shared hosting server or something like that? Sorry, I just assumed you were on your own local computer.

To set a password for a non root account, you should be able to just enter:

```

mysqladmin -u your_username password ThisIsThePasswordThatIWantToUse!!

```

Come to think of it, you can set or change your password through phpMyAdmin as well. I haven't got it installed at the moment, but there should be an option in the far left column to change your account.

---

### Post by lahp on 2008-09-22
lol i am on my own server =D and i tried tht other code didnt work either

---

### Post by lahp on 2008-09-22
mysqladmin: Can't turn off logging; error: 'Access denied; you need the SUPER privilege for this operation'

---

### Post by stickmangumby on 2008-09-22
Haha :)

Did you find an option to set or change your database password in phpMyAdmin?

---

### Post by lahp on 2008-09-22
noooo as far as i am aware from preivous experience i think i need to get to the config file (i used it on windows)

---

### Post by Monotoko on 2008-09-22
why doesnt sudo work?

and linux is far differant to windows, ignore any windows experiance when using linux, because its probably gonna be differant.

---

### Post by lahp on 2008-09-22
i dont know why i am using server edtion if tht makes a dif any way i off to bed email me if u can [email]treemonkey13@hotmail.com[/email] cheers 

i just need to set a pass!!!! :'(

---

### Post by cariboo on 2008-09-22
To log into phpmyadmin you have to use root as the user name and the password you setup when you installed mysql.

You should make sure you have mysql running by typing in a terminal:

```
ps ax | grep mysql
```

The out put should be something like this:

```
ps ax | grep mysql
 4998 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 5040 ?        Sl     0:07 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 5041 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
10294 pts/0    S+     0:00 grep mysql
```

If mysql is running, in the same terminal see if you can access the mysql console:

```
mysql -u root -p
```

When it asks for a password, enter the password you setup when you installed mysql. TO exit the mysql console type: \q

If all of the above worked you should be able to log into phpmyadmin.

Jim

---

### Post by lahp on 2008-09-23
cool i can access phpmyadmin but it isnt secure it has no password i just eneter my route user name (sudo name) and it opens

---

### Post by lahp on 2008-09-23
ok i have forgotten my password i used to set up mysql lol is there any way i can reset it? like reinstall or what?

---

### Post by lahp on 2008-09-24
any one hav any ideas at all ?

---

### Post by Herrlos on 2008-10-15
> **lahp said:**
> any one hav any ideas at all ?

> sudo apt-get autoremove mysql-server mysql-client
> sudo apt-get install mysql-server mysql-client
> sudo mysqladmin -p password -u root YourNewPassHere

it was useful where i got this error

---

