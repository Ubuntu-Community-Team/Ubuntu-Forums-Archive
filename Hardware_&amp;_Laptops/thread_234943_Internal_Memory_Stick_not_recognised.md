---
title: "Internal Memory Stick not recognised"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by clarembutler on 2006-08-12
Please can anyone help with this problem or point me to a solution on the forums.  I have a vaio laptop, running Dapper and most things work perfectly.  However the two things that don't are the internal memory stick is definately not being recognised and the screen resolution resolutely refuses to work at 1280 x 768.  I currently have it at 1366 x 768 which is the best I can get.  Any help on these problems gratefully received.

---

### Post by gholen on 2006-08-12
You'll need ro recompile upur kernel in order to make MMC/SD-slot working.
And for the resoultion problem, have a look at 915resolution, and read the man-page careful!

These link may be helpful, but remember, do *NOT* uninstall your current kernel!

[http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657)  <-- kernel compile HOWTO

[http://ubuntuforums.org/showpost.php?p=1296169&postcount=2](http://ubuntuforums.org/showpost.php?p=1296169&postcount=2)  <-- Kernel compile tips!

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)  <-- 915resolution homepage

---

### Post by clarembutler on 2006-08-12
Many thanks re 915resolution.  Now working.  Great.

I will try the kernel stuff now.

---

### Post by clarembutler on 2006-08-14
Sadly the kernel rebuiling hasn't produced results (lost my wifi).

Has anyone got any other suggestions?

---

### Post by gholen on 2006-08-14
Okey....
Did you make the old config?
In network, make sure that your card is listed as module or to be compiled with the kernel...

---

### Post by clarembutler on 2006-08-15
> **gholen said:**
> Okey....
Did you make the old config?
In network, make sure that your card is listed as module or to be compiled with the kernel...


Sorry, bit of a newbie here, with enforced idleness.  Um what old config?

---

### Post by clarembutler on 2006-08-16
> **gholen said:**
> Okey....
Did you make the old config?
In network, make sure that your card is listed as module or to be compiled with the kernel...

I have now installed Edgy-Knot1, with kernel 2.6.17.5.  Wireless woprks but MS doesn't still.  Is there a way to force it to mount?

---

### Post by clarembutler on 2006-08-20
Back to Dpper.  Would love it if someone could help.

---

