---
title: "MySQL error"
date: 2008-11-09
forum: General Help
---

### Post by CaseWestern on 2008-11-09
Hi All:

I installed mysql server using sudo apt-get install mysql-server from the terimal.  And it did install on my computer and when I am trying to access mysql it says

```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock
```

I have been trying to figure this out quite from some time.  I actually gave up last week and installed XAMPP.  But now I have to access mysql from shell and when I tried to install it again, it gives the above mentioned error.

I would appreciate if any of you guys can provide me some solution.

Thanks in advance

---

### Post by d_in_Conduct on 2008-11-09
Be sure you have installed mysql client also.  Then go to mysql.com and read up on setting up the system.  You have to set yourself up as a user and give yourself all the necessary permissions, privileges, and password;  doing this all as root.

---

### Post by CaseWestern on 2008-11-09
> **d_in_Conduct said:**
> Be sure you have installed mysql client also.  Then go to mysql.com and read up on setting up the system.  You have to set yourself up as a user and give yourself all the necessary permissions, privileges, and password;  doing this all as root.

Do you think its because I already have MySQL running with XAMPP?

---

### Post by CaseWestern on 2008-12-04
> **CaseWestern said:**
> Hi All:

I installed mysql server using sudo apt-get install mysql-server from the terimal.  And it did install on my computer and when I am trying to access mysql it says

```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock
```

I have been trying to figure this out quite from some time.  I actually gave up last week and installed XAMPP.  But now I have to access mysql from shell and when I tried to install it again, it gives the above mentioned error.

I would appreciate if any of you guys can provide me some solution.

Thanks in advance

I found the solution for this....actually you have to stop the mysql dameon already runinng on your system if you installed any....

here is the code

```
/etc/init.d/mysql stop
```

you can do that only in super user mode......after stopping this dameon start the xampp server again using

```
/opt/lampp/lampp start
```

---

