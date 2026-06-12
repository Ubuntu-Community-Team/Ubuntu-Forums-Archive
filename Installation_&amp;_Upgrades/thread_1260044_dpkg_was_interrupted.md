---
title: "dpkg was interrupted"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by saneej on 2009-09-07
While installing opera 10 (Already I'm having 10 beta), Installation got struck. Then I have cancelled installation. Now following error comes in Synaptic Package manager.

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Pls help me 2 overcome this prblm.

---

### Post by saneej on 2009-09-07
The problem automatically solved out. I didnt do anything. But I tried s.p.m againe. Its works. Pls tell me If I got this problem again what will I have to do?

---

### Post by imhotep59 on 2009-09-07
Hello, quite simple, you will just have to do what is asked in your first post:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
```
So run in a terminal
```
sudo dpkg --configure -a
```

---

### Post by saneej on 2009-09-07
Oh man. Thank u. I tried with RUN APPLICATION instead of trying in terminal. Sorry. Thanx. Nw ok. I tried. Options are there.

---

### Post by Pastor_JW on 2009-09-09
> **imhotep59 said:**
> Hello, quite simple, you will just have to do what is asked in your first post:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
```
So run in a terminal
```
sudo dpkg --configure -a
```
I have this too and the sudo dpkg --configure -a just runs off into never never land.  The problem package for me was/is turboprint.  Can't get rid of that either.  Machine just sits and does nothing now for more than eight hours.

---

### Post by imhotep59 on 2009-09-09
First, you have to verify if turboprint was installed, at least in part. Try:
```
whereis turboprint
```
and give the result

---

