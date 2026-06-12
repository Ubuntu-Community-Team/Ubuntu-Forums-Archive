---
title: "Where do I find system specs in ubuntu."
date: 2008-05-20
forum: Hardware
---

### Post by thabo on 2008-05-20
Anybody know where I can find a program to display system specs ie cpu type and speed, ram, etc.
Ive looked at xchat but it does not seem to work for this.

Thanks.

---

### Post by NightwishFan on 2008-05-20
Try system monitor or hardinfo.
```
sudo apt-get update && sudo apt-get install hardinfo && hardinfo
```

---

### Post by thabo on 2008-05-20
> **NightwishFan said:**
> Try system monitor or hardinfo.
```
sudo apt-get update && sudo apt-get install hardinfo && hardinfo
```

Thanks a lot Nightwish.
Installed and its impressive all the info it give- times its been booted etc!

---

### Post by NightwishFan on 2008-05-20
Yeah I like it a lot, also light on dependencies. I believe it was recommended by the xfce4 team.

---

### Post by wootah on 2008-05-20
Wow this is a very impressive tool! +1 Nightwish

---

### Post by ZachMitchell on 2009-03-08
> **NightwishFan said:**
> Try system monitor or hardinfo.
```
sudo apt-get update && sudo apt-get install hardinfo && hardinfo
```
Thanks! I've been looking for something like this.

---

### Post by ASCHYIEL on 2009-07-01
hardinfo Works like a charm.  Thanks man.  ^^

---

### Post by NightwishFan on 2009-07-02
Enjoy! ;)

---

### Post by SPARTAN-118 on 2009-08-10
Great, thanks, been looking for something like this! 
System Monitor just isn't detailed enough, and this program shows you *everything*.

---

### Post by Dillanm on 2009-10-24
Really impressive program! Loads of detail. Cheers :)

---

### Post by dalekirkwood on 2011-02-07
Great Program, Thanks

---

### Post by lostmonster on 2011-03-29
I agree.  This program works great in explaining your system in full.

---

### Post by fernandogarcez on 2012-01-23
You can also just do to list it:

sudo lshw

Regards,

---

### Post by TheBigDog on 2012-02-15
:D  Great info!  I added this to my "folder of all Ubuntu knowledge."  I am trying to learn the details of Linux (specifically Ubuntu with some Mint and Fedora thrown in).  While it is more "accessible" than Windows, it is taking some time to understand the machinations of the kernel and to "relearn" and understand the depths of the "command prompt".  Kudos aplenty for this report tool!

---

### Post by coldraven on 2012-02-15
What I do on a new install is this:
```
sudo lshw > hardware.txt
```Then you will have a handy list in a file called hardware.txt in your home folder.

---

