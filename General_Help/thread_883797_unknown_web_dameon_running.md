---
title: "unknown web dameon running"
date: 2008-08-08
forum: General Help
---

### Post by papabill on 2008-08-08
In an attempt to set up my web server, I installed apache2, mysql, php, perl, and phpmyadmin. The configuration files turned out too much for me to figure out, so I (thought) I uninstalled everything and installed XAMPP in their place.

However, now when I try to re-start apache2 after a configuration change, I get the following message: 
```
root@Forum:/home/bill# /opt/lampp/lampp stopapache
XAMPP: XAMPP-Apache is not running.
root@Forum:/home/bill# /opt/lampp/lampp startapache
XAMPP: Another web server daemon is already running.

```
I have even tried uninstalling and re-installing XAMPP.

I have tried everything elseI know to find out this other web server, but cannot. 

Ideas? Suggestions?

Thanks

---

### Post by Taxman415a on 2008-08-08
I don't know anything about that lampp stopache command, but apparently it is either missing the process you have running or whatever is making the start process think there is one running is wrong. Have a look through the output of ps -ef until you are confident there is nothing running. ```
ps -ef|grep apache
``` might help, but you may want to grep for other pattern or look through the whole output by hand to make sure you don't miss anything. If you find one, kill it with kill -9 and the process id. Basically uninstalling a package won't typically kill running processes.

---

### Post by papabill on 2008-08-08
Thanks. I have figured out that I don't have enough knowledge about Linux to proceed with my project. There aren't enough BBSs like the one I am trying to set up to get very much support from, so I guess I'd better give up on the project all together.

Thanks for your help.

---

