---
title: "Cannot Write to CD/CDRW - HELP!"
date: 2006-09-23
forum: Hardware &amp; Laptops
---

### Post by anpan on 2006-09-23
Can someone give me suggestions as to how I can write data files to the CD?  I have Ubuntu 5.10.  The CD is owned by the root,  I tried to change the owner to user, but it doesn't let me change it.  Is there a way to change from the root to user so I can write to the CD?

Thanks.

Ted

---

### Post by JAwuku on 2006-09-23
I'm not sure, but you could try to change the read/write permissions of /media/cdrom i.e.

```
chmod 777 /media/cdrom
```

if you type **[COLOR="Purple"]ls -l /media[/COLOR]** what does it show?

Mine shows :

```
ls -l /media
total 12
lrwxrwxrwx 1 root root       6 2006-09-23 02:20 cdrom -> cdrom0
drwxr-xr-x 2 root root    4096 2006-09-23 02:20 cdrom0
dr-xr-x--- 1 root plugdev 8192 2006-09-14 10:19 windows

```

---

### Post by srirammurali on 2006-09-23
sudo nautilus /media/
enter your password when prompted and change the properties of the link /media/cdrom to 777 (read-write-execute for all users)

---

### Post by anpan on 2006-09-28
To: JAwuku

When I entered chmod 777 /media/cdrom, it says /media/cdrom:Read only File System.  When I entered ls -1 /media, it shows -

total 5
1rwxrwxrwx 1 root root  6 2006-09-24 03:08cdrom - > cdrom0
dr-xr-xr-x 1 root root 214 1969-12-31 16:00 cdrom0


To: Srirammurali
At Properties, it shows 555 for the Number, but I can't change anything in this box, even tho it shows root.


Thanks to you both for responding.  I await your reply with bated breath...thanks again.

Ted

---

### Post by srirammurali on 2006-10-17
i just tried it on my system, got the same problems... try unmounting any disc that might be in the drive and then give it a try

---

### Post by jefuchs on 2006-11-01
I searched all through this forum, and couldn't get an answer.  Finally found this on the web...

[http://www.novell.com/coolsolutions/feature/11501.html](http://www.novell.com/coolsolutions/feature/11501.html)

Worked like a charm.  I'm burning a CD now!

---

### Post by srirammurali on 2006-12-05
wow.. real gud link buddy...

---

