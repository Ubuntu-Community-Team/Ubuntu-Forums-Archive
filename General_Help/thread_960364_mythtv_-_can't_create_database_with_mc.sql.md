---
title: "mythtv - can't create database with mc.sql"
date: 2008-10-27
forum: General Help
---

### Post by Goregasm on 2008-10-27
Hello. I've been using this forum alot to help me in the transition to ubuntu and this is my first post because it's the first problem I can't find a solution. 

After I tried mythbuntu I left windows for good, but I preferred to try Ubuntu 8.10 beta and manually install mythtv. I've installed both sql and mythtv with apt-get and when trying to build the database manually with:

```
root@server:/home/goregasm# mysql -u root -p < /usr/share/mythtv/sql/mc.sql
```

I enter the password and then I get:

```
ERROR 1064 (42000) at line 1: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysqladmin  Ver 8.41 Distrib 5.0.67, for debian-linux-gnu on i486
Copyright (C) ' at line 1
```

Now I'm stuck, so any help would be great.

---

### Post by Goregasm on 2008-10-30
Anyone? I think this might me a simple problem (that I don't know how to fix)

---

### Post by sdowney717 on 2008-10-30
how does me-tv work for you?

[http://linux.softpedia.com/get/Multimedia/Video/Me-TV-29756.shtml](http://linux.softpedia.com/get/Multimedia/Video/Me-TV-29756.shtml)


as for mysql, can you login to mysql from the terminal using the user name and password?

---

### Post by Goregasm on 2008-10-30
Hey, thanks for your attention but I just gave up. I purged the mythtv installation but now it does not install again. Don't waste your time because I won't waste mine. I'll download mythbuntu 8.10 (or ubuntu 8.10 final and try again) that should be out in the next few days, and I'll use that.  

Just for the record, mysql works fine, and due to the error, all it seems it's some kind of error at line 1 of mc.sql (that's included in the mythtv installation files).

Thanks anyway.

---

