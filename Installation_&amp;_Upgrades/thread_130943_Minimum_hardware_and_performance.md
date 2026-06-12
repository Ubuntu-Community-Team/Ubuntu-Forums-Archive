---
title: "Minimum hardware and performance?"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by kmcfarlane on 2006-02-15
I tried installing Ubuntu 5.10 on an old laptop, to see if an old laptop could be made useful.  I used the default installation.  The laptop has a P II, 266MHz, 96MB RAM, and a 4.3GB drive.  The install completed with only one error (did not update clock from ntp...).  Everything I tried seemed to work (including network access).

However, it is very slow: 110 seconds to bring up the GUI.  4-5 minutes to bring up an OpenOffice app.

Is this to be expected?  Would it help to strip out stuff like Bluetooth support (!)?

Does someone know the minimum for decent performance (e.g <10 seconds to bring up an OpenOffice app)?

---

### Post by K.Mandla on 2006-02-15
You might try Xubuntu, which is lighter than the default desktop. I've put Ubuntu on a 233mhz P2 with 128Mb and it was way too slow. Xubuntu was better, and you get enough goodies to keep you busy.

I think after 200Mhz (and the appropriate amount of memory), things start to fall off. Xubuntu on a P1 120Mhz with 40Mb was way too slow. For that, I had to go to Damn Small Linux. But DSL flies even on that machine. It's not nearly as friendly as Ubuntu, but it's good for showing off to friends. :D

---

### Post by az on 2006-02-15
[QUOTE=kmcfarlane]However, it is very slow: 110 seconds to bring up the GUI.  4-5 minutes to bring up an OpenOffice app.)[/QUOTE]

110 seconds is not at all bad!

4-5 minutes for open office is because ituses a lot of memory.  Can you add some more memory to the box?  If not, don't use Open office.

I run Ubuntu on a pI 166, 96 megs of ram with a 2.1 giog HDD.  It is slow.

Xfce is faster, but on a P1, it is not so impressive.  Try icewm.


[QUOTE=kmcfarlane]
Would it help to strip out stuff like Bluetooth support (!)?[/QUOTE]

No.  There are no bluetooth services started up and the kernel modules are not loaded unless you have bluetooth hardware.  It's already like it's not even there...

[QUOTE=kmcfarlane]

Does someone know the minimum for decent performance (e.g <10 seconds to bring up an OpenOffice app)?[/QUOTE]

PII 400Mhz with a 512k cache with 128 megs of memory.  I would say that is the inflection point on the performance versus hardware scale.

---

### Post by kmcfarlane on 2006-02-15
Thanks for the comments.  The laptop will hold 160MB of RAM.  I'll price that.  I was looking for a way to collect 'obsolete' laptops and make them useful for people who have no computer.  So the 'inflection point' comment gives me a good guide as to what's worth collecting.

---

