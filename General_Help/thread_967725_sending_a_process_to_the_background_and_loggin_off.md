---
title: "sending a process to the background and loggin off"
date: 2008-11-02
forum: General Help
---

### Post by Tadhg on 2008-11-02
I have a headless server running at home. I want to be able to ssh in start a program to run in the background, log out, and be able to log back in and bring it to the front again (having it run in the background all along). 

How do I do this?

---

### Post by scragar on 2008-11-02
If the process is running in the foreground, you can send it to the background with the ctrl+Z combo of keys.
If you want to start the process in the background you can end the command with a space followed by an ampersand( & ), so for example, starting lynx in the background:
```
lynx &
```

to bring a process back to the forground you use the **fg** command, it accepts  process names.
Use ```
ps
``` to check the processes your running.

And a sample of it(I googled a random set of letters to find this image, it didn't intrest me, it was the first result on google image search):
```
**$ wget http://www.freewebs.com/xbookhehe/gsdg.bmp**
--2008-11-02 14:10:57--  http://www.freewebs.com/xbookhehe/gsdg.bmp
Resolving www.freewebs.com... 204.2.183.2
Connecting to www.freewebs.com|204.2.183.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1626806 (1.6M) [image/bmp]
Saving to: `gsdg.bmp'

 0% [                                       ] 0           --.-K/s              **^Z**
[1]+  Stopped                 wget http://www.freewebs.com/xbookhehe/gsdg.bmp

**$ ps**
  PID TTY          TIME CMD
  667 pts/0    00:00:00 bash
  686 pts/0    00:00:00 wget
  688 pts/0    00:00:00 ps
**$ fg wget**
wget http://www.freewebs.com/xbookhehe/gsdg.bmp
10% [===>                                   ] 176,884     1.37K/s  eta 18m 35s

```

---

### Post by Tadhg on 2008-11-02
if i do that though, once i log out, the process is killed is it not?

---

### Post by scragar on 2008-11-02
Huh, I tried it on a tty, and I was unable to log out with tasks running...
```
**$ w3m google.com**
[1]+  Stopped                 w3m google.com
**$ exit**
Logout
There are stopped jobs
**$**
```
I don't think you'll be able to do what you want then,

Either way it's nice to know about basic job controll.

---

