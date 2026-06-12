---
title: "Mysql fails to start at bootup"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by Woobun2 on 2008-12-07
Hi there,

I have installed Mysql on Ubuntu 7.10 and everything was working fine. But I wanted to try to log to the database remotely so I've changed the /etc/mysql/my.cnf file by changing the bind-address to my Ubuntu-PC's address. Great I can access the database remotely. The thing is now that mysqld doesn't start up automatically anymore. I've taken a look at the syslog and found out that the problem was somehow that mysqld was failing to start up cause it couldn't be bound to the address of my PC since mysql tries to start up before my PC can get its IP address through DHCP. I've tried to change the order in which things start (putting mysql towards the end of the   daemons to launch in the different run levels but it didn't change the order  and mysqld still tries to get started before I can get my IP address. Any ideas ?

---

