---
title: "enable ieee 1394"
date: 2008-08-27
forum: General Help
---

### Post by tsumeb on 2008-08-27
HI I new to Ubuntu,
I'm in desparate need of help, I am going on holiday shortly to Namibia and would like to get my ieee 1394 up and running every thing else works a treat.
I replaced my HDD with a larger unit and installed Hardy Heron (i386) I find it realy good (unlike Vista)
Laptop Acer Extensa 5220
1.5 gb Ram
Canon DCR-TRV230E
4X4 Firewire cable (new cable works under Win Vista)
Kino installed

george@george:-$ lsmod | grep 1394
dv1394                  20536 0
raw1394                29144 0
ochi1394               33584 1 dv1394
ieee1394               93752  4 dv1394,raw1394,sbp2,ochi1394

This is as far as I can get,can some one help please

---

### Post by LateNiteTV on 2008-08-27
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

google will typically answer faster than anyone on here.

---

### Post by tsumeb on 2008-08-29
Thanks any way
tried all these sugestions with no luck
Going to load Win XP on shortly.

---

### Post by remeeraz on 2008-10-13
> **tsumeb said:**
> Thanks any way
tried all these sugestions with no luck
Going to load Win XP on shortly.

Instructions on this [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) page are wrong. I will alter them soon.

follow my instructions carefully in this thread.

[http://ubuntuforums.org/showthread.php?t=946708](http://ubuntuforums.org/showthread.php?t=946708)

:popcorn:

---

