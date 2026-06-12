---
title: "hard drive with errors"
date: 2010-09-01
forum: Hardware
---

### Post by cholericfun on 2010-09-01
Hi

a friend has a serious problem with her laptop,
basically her hard drive is full of errors, the BIOS
is saying something like "HD status BAD" and booting into her standard Windows is impossible.

so she asked me to help her with a LiveCD, however i could not really do anything so far. Heres a few questions:

when i boot from a liveCD it takes ages to boot because the CD is detecting errors on the hard drive. Is there a way to skip this check so that booting takes only a few minutes instead of half an hour?

when in a live environment, the hard drive does not appear under /dev/
so i guess the system decided the HD is dead. Gparted takes forever to look for harddrives as well and eventually declares that no HD has been found.
Is there a way to force the system to accept the HD and mount it? Can i even try fsck and testdisk with the HD not listed in /dev/  ?

ok
thanks for your help

---

### Post by carl4926 on 2010-09-01
Try a live cd like Parted Magic which offers lots of tools to help repair. But darn. HD's a so cheap, don't wast your life with it. Go buy a new one:D

---

### Post by cholericfun on 2010-09-01
yes, its not really about panic-my-hd-is-broke,
but i thought it would be good to collect a few ideas on how to approach
such a problem. I presume partetMagic tools would be available through the repositories as well. still i'm not sure what to even look for. 
plus knowing how to boot into a liveCD without endless errors and checking of the HD would be nice as well. Recently while installing Lucid i had a similarly irritating problem that the liveCD would not boot (whithin an hour patience) after formating to ext4 because of apparent HD errors (something about raid array where there is no raid array).

---

### Post by carl4926 on 2010-09-01
[http://lmgtfy.com/?q=parted+magic](http://lmgtfy.com/?q=parted+magic)

---

### Post by cholericfun on 2010-09-09
anyone any ideas how to read a disk not listed in /dev ?

---

### Post by cascade9 on 2010-09-09
Does the drive appear in the BIOS?

---

### Post by cholericfun on 2010-09-09
I can't really check now, last time is saw it the BIOS sayd the HD was "BAD"

---

### Post by cascade9 on 2010-09-09
I'm yet to see a BIOS say that,. interesting. 

Anyway, if the BIOS cant find the HDD (and I would guess if the BIOS has declared the HDD 'bad') then you wont be able to mount it, no matter what you do.....beg, pray, swear, cajole, or threaten.

---

