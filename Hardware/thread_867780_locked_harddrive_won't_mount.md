---
title: "locked harddrive won't mount"
date: 2008-07-23
forum: Hardware
---

### Post by imshag on 2008-07-23
G'day guys
I bought a cheap secondhand laptop online, the reason I got it so cheap was because it couldn't find the operating system, so I swapped hard drives and easy as, all go, heres where it gets ugly, the laptop came with an external dvd writer so I had it all plugged in looking to play with it, I had to restart the laptop so I did, when I did it seems the bios locked the hard drive, no os found. I can see the drive in device manager but can't mount or  see it anywhere else. there is a password for the bios that the old owner has no idea of (didn't even know what the bios was) It won't stop me from starting the laptop just entering the bios. Hard drives won,t show up on any other laptop or usb case. Is there any way i can save the hard drives? and/or break the bios password? Laptop is HP Pavilion ze4500 at the moment running Ubuntu 7.10 live cd. Drives are both Hitachi Travelstar. 

Cheers in advance,
shane

---

### Post by Envirotech on 2008-07-23
You need to remove the cmos battery to reset the bios.  That may or may not reset the harddrive lock depends if the laptop uses a tpm chip ( [http://en.wikipedia.org/wiki/Trusted_Platform_Module](http://en.wikipedia.org/wiki/Trusted_Platform_Module) ). if it does then you may be SOL.  [http://h10032.www1.hp.com/ctg/Manual/c00246219.pdf](http://h10032.www1.hp.com/ctg/Manual/c00246219.pdf) is the service manual.  Hope this helps.

---

### Post by imshag on 2008-07-25
Cheers, removed the cmos battery (laptops are a mission) didn't reset the bios password but did let me choose a diagnostic check at startup which evidently unlocked the hard drive, so I'm going to take it as a win for the good guys, Cheers for the help, Shane

---

