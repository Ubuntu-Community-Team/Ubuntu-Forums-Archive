---
title: "Appletalk printer?"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by Sn1pe on 2005-07-05
I recently pulled the old Apple Personal LaserWriter 320 out of the attic and hooked it up to an Asante Micro Asanteprint via appletalk(over phone lines) and into my switch (via ethernet from the Asanteprint).  My OSX powerbook detected the printer and printed off a beautiful page!  (this printer is amazing for b/w).  

My question:  How do I go about installing this printer in Ubuntu?  The only protocol atm that it shares on is appletalk... I'm still trying to hack my way into the printserver to see if it has any other options.  Anyone using an appletalk printer?

---

### Post by mneptok on 2005-08-28
I just wrote up a how-to on this subject on the Ubuntu wiki. Have a look [here](https://wiki.ubuntu.com/AppleTalk).

HTH.

---

### Post by jamescoy on 2007-06-30
I just attempted to follow these instructions and go this:

james@james-desktop:~$ sudo apt-get install netatalk
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
netatalk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
james@james-desktop:~$ nbplkup
                  james-desktop:AFPServer                          65280.16:128
                  james-desktop:netatalk                           65280.16:4
                  james-desktop:Workstation                        65280.16:4

As you can see, my printer isn't listed, but it's working fine on the Mac side of things. Is there something I've missed doing here?


I installed netatalk with apt-get and did no configuration. 

Thanks.

---

