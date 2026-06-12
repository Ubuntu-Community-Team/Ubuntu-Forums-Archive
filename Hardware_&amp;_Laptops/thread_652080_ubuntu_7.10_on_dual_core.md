---
title: "ubuntu 7.10 on dual core"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by kichu7 on 2007-12-28
Hello,

 I have a lenovo laptop - model 3000 G400.

 It has a intel pentium dual core processor. I want to know which ubuntu should i install on that.

=============================
ubuntu-7.10-desktop-i386.iso   

    or
ubuntu-7.10-alternate-amd64.iso
=============================

Please reply... I think dual core is 64 bit, so the second one is correct. Please help me... :)

---

### Post by taurus on 2007-12-28
The first file will give you the 32bit while the second one will give you the 64bit.  On the other hand, there is a desktop CD for 64bit and an alternate CD for 32bit as well.  You can install either 32bit or 64bit on your machine.

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/)

---

### Post by omegamike3 on 2007-12-28
You could install either of these as the the dual core processors can run both 32bit and 64bit OS's. There are advantages and disadvantages to both. However, if you're just starting out, I would recommend you go with the 32bit version or 'ubuntu-7.10-desktop-i386.iso' You'll have fewer program compatibility issues, especially for the 'essential' things nowadays, like flash and codecs.

---

### Post by kichu7 on 2007-12-28
HAi..thanks for that quick reply.

 One of my frnd installed the 32 bit desktop version on the same laptop ( lenovo 3000 G400 pentium dual core). But he telling, his some applications not working like klipper, knotes, kedit..
and it is showing some error related to "bit"( i mean compatibility issues with 32 & 64).

So shall i proceed with 64 bit desktop version,

==============
ubuntu-7.10-desktop-amd64.iso 
================

Will i get those klipper,knotes & kedit all things working..? Please reply..:)

---

### Post by omegamike3 on 2007-12-28
> **kichu7 said:**
> One of my frnd installed the 32 bit desktop version on the same laptop ( lenovo 3000 G400 pentium dual core). But he telling, his some applications not working like klipper, knotes, kedit..
and it is showing some error related to "bit"( i mean compatibility issues with 32 & 64).


Those, to my knowledge, should run just fine on a 32bit system. It's possible that he is receiving errors because those are KDE based applications. KDE applications can be run in GNOME just fine as long as the KDE dependencies they need are there. BTW, KDE and GNOME are sort of the equivalent to explorer in windows, giving you your desktop environment (ie. toolbars, menus, etc) Ubuntu uses GNOME by default, whereas Kubuntu uses KDE as the default environment.

---

### Post by kichu7 on 2007-12-28
Oh.. so that is the case... So during login prompt if i choose KDE instead of GNOME, may it work well...right...?

Also can you tell me the disadvantages of using 64 bit ubuntu in pentium dual core..?:KS

---

### Post by omegamike3 on 2007-12-28
> **kichu7 said:**
> Oh.. so that is the case... So during login prompt if i choose KDE instead of GNOME, may it work well...right...?

Also can you tell me the disadvantages of using 64 bit ubuntu in pentium dual core..?:KS

Yes, choosing KDE would be one way of getting it to work. For now, the only real advantage you'll get out of using 64bit is with 64bit applications. That is, programs that are specifically designed to take full advantage of this type of OS. For most users, at present time, 64bit will have little affect. The most notable and apparent thing that the average user notices when using a 64bit OS (depending on the OS) is the full use of RAM available past 4GB. Though, most 'average' users aren't going to have a machine with this much memory. You can check out Wikipedia for more info on 64bit:

[http://en.wikipedia.org/wiki/64-bit]("http://en.wikipedia.org/wiki/64-bit")

---

### Post by kichu7 on 2007-12-28
Oh.. Thanks for that info..

I have one more query. How can i install KDE on ubunutu..Bcoz now on laptop only GNOME is showing..

---

### Post by taurus on 2007-12-28
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by kichu7 on 2007-12-28
thank you so much... you are really very helpful...god bless you... hav a great new year...:guitar:

---

