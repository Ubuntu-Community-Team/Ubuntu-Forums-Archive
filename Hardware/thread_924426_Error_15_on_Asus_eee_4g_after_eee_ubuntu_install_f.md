---
title: "Error 15 on Asus eee 4g after eee ubuntu install failed"
date: 2008-09-19
forum: Hardware
---

### Post by Cobbs on 2008-09-19
Okay, I was using a usb stick to load the iso for eee ubuntu on to my Asus eee 4gb.  I used unetbootin to create the bootable usb drive, booted into the live "cd" and continued with the prompt to install ubuntu.  A few seconds short of finishing the install, an error message came up that the cd was dirty and the install could not continue (weird, since I am using a usb drive..not a cd).  I tried to reboot with the usb in the computer and trying to boot from the HDD but I am met with a black screen and "error 15".  I googled it couldn't really find anything helpful, is there a way to correct this? I am assuming that there is no OS on the system now, but if I can install past it with ubuntu, that would be great.  I'm hoping I didn't ruin my eee... Any suggestions would be most appreciated, I am at a loss what to do at this point!

Thanks in advance!

---

### Post by Cobbs on 2008-09-20
**update** I tried to re-install using a different stick (hoping that I would be able to boot past it), however I got a new message.

SYSLINUX 3.53 Debian-2007-12-11 EBIOS Copyright 1994-2007 H. Peter Anvin
Could not find kernal image: linux
boot:_

So I am assuming that my iso file is not being transfered by unetbootin?

---

### Post by fuzzbuzz85 on 2008-11-10
Hiya, I'm having exactly the same problem. I had an errno 5 on install, then re-did the unetbootin on the same usb, but with 8.04.1 this time. Tried to reinstall but only got error 15 the first time, then the same message that you got the second time, then finally error 15 again. I'm thinking it's that unetbootin didn't manage to transfer a grub properly to the usb... did you manage to solve this?

---

### Post by Cobbs on 2008-11-10
Aye, the solution was to run the whole operation from a windows machine.  You are correct to assume that the grub is not being transfered to the usb boot stick, I found in a random post in another forum that apparently unetbootin will not complete step 3 (the grub part) when being run from a linux system.

So I took my iso down to the computer lab, installed unetbootin, ran the process with the usb stick and iso, and my eee booted right into the installation.

Good luck mate,

Cobbs

---

### Post by fuzzbuzz85 on 2008-11-13
Awesome! Thanks for that I'll give it a go!
 Cheers :)

---

### Post by sidewalkcynic on 2009-01-21
> mtools not found. This is required for USB Drive install mode.
Install the "mtools" package or your distribution's equivalent.

7z not found. This is required for either install mode.
Install the "p7zip-full" package or your distribution's equivalent.

UNetbootin gave me these two messages before run, after reboot I got the error 15.

I was attempting to install to hard disk running Ubuntu 7.04 CD. Because 7.04 is out of date I cannot recover the mtools or the 7z.

I do not have access to a Windows computer???

any possibilities, out there.

---

### Post by cmay on 2009-01-21
try the alterantive textbased installer cd first. 
i have had a tread on these problem. i found out it was a bug in the ubuntu installer and it is also reported as such. i have a computer i fixed where is could for the life of me not get installed ubuntu from dvd and it is too old to boot from usb. i ended up using the alernative gobuntu textbased installer which does not have this bug. then i upgraded from that to ubuntu testing (jaunty jackalope) . until the bug is fixed i do not use ubuntu anymore. i have also found that after i swithed the dvd drive i can install ubuntu on this one computer. but it does it on all other computers i have as well. even the new one i picked up from the store a good 2 month ago which told me it could not be the dvd drive as in it in fact was new. i use now a singel ubuntu 8.1.0 image on usb stick as live system but i cant install in other ways than using the old 7.0.4 textbased installer i got from linux magazine or the newer gobuntu textbased installeer. hope you find a solution. good luck

---

### Post by sidewalkcynic on 2009-01-21
I can't write CD's - so, are you saying I can use the Gobuntu iso with the UNetbootin?

---

