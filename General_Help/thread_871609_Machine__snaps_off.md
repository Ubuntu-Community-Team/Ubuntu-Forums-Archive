---
title: "Machine  snaps off"
date: 2008-07-27
forum: General Help
---

### Post by no-1-uno on 2008-07-27
Hello and thankX ahead of time.

I am running hardy 8.04 on a dell latitude D610.

When I try to open
```
system/admin/login window
```
My machine sorta snaps off well not all the way off but it goes to a black screen then to another black screen with a few commands and a flashing prompt. I have to hit the power button then the machine restarts. I have not written down the lines because there are too many but I can if need be.

I have been running Linux for about a month now and really like it. The only thing I changes on the log window was turning the sound off.

When trying to open the window for login open and closes very fast and then it is almost off instantly. This seems to be the only thing that causes this problem.

ThanX again ahead of time

---

### Post by jimv on 2008-07-27
what do you get if you type this?

gdm start

---

### Post by no-1-uno on 2008-07-27
tojo@ubuntu:~$ gdm start
gdm[9067]: WARNING: GDM file gdm-daemon-config.c: line 2033 (): Cannot run seteuid to 0: Operation not permitted
GDM file gdm-daemon-config.c: line 2033 (): Cannot run seteuid to 0: Operation not permitted
tojo@ubuntu:~$ 


As a new user I have no clue about this

ThanX

---

### Post by jimv on 2008-07-27
Try this:

sudo /etc/init.d/gdm start

---

### Post by no-1-uno on 2008-07-27
tojo@ubuntu:~$ sudo /etc/init.d/gdm start
[sudo] password for tojo: 
 * Starting GNOME Display Manager...                                     [ OK ] 
tojo@ubuntu:~$

---

### Post by no-1-uno on 2008-07-27
be back in a little while going for a nap

---

### Post by no-1-uno on 2008-07-27
Bump

---

