---
title: "Insane boot time - 149 seconds of NOTHING"
date: 2011-05-18
forum: Hardware
---

### Post by Sorensiim on 2011-05-18
After installing a new Radeon 5750 in my desktop PC, the boot time has been insanely long. The first 149 seconds after grub involves absolutely no disk or CPU activity :(

I'm running 11.04 on a pretty powerful machine, but some sorta snag is slowing down the boot immensely. 

Bootchart: [Http://www.sorensiim.dk/stuff/forumpix/Whitey-ubu-natty-20110518-1.png](Http://www.sorensiim.dk/stuff/forumpix/Whitey-ubu-natty-20110518-1.png)

How do I skip those 149 seconds of absolutely nothing?

---

### Post by lithopsian on 2011-05-18
Looks like the same problem that several other people have come across.  System hangs for ages at kernel initialisation, and possible on hardware detection.  I haven't seen anyone with a solution.

---

### Post by Sorensiim on 2011-05-18
Damn... I'm wondering if a fresh install of 10.10 would solve it...

---

### Post by Sorensiim on 2011-05-20
To hell with it, I did a fresh install of 10.04LTS this morning. 32 seconds boot time in stead of 3 minutes and change...
[http://www.sorensiim.dk/stuff/forumpix/Whitey-ubu-lucid-20110520-8.png](http://www.sorensiim.dk/stuff/forumpix/Whitey-ubu-lucid-20110520-8.png)

Can't decide if I should start trimming and tuning the boot sequence now... :D

---

### Post by lithopsian on 2011-05-21
Not so bad.  Is ureadahead profiling on that bootchart?

---

