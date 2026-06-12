---
title: "new install, freezes at boot"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by jdarnel2 on 2005-05-07
Hi everyone,

I'm new to the Linux and Ubuntu world.  I've used Ubuntu, the previous version, on my iBook.  It installed beautifully, all is still well with that install.

I recently built a new PC.  The hardware is as follows:

ABIT ATI x600 PRO PCI-E vid card
ABIT an8 motherboard
ATHLON 64 3000+ 
1 gig of Corsair RAM
160 GB Seagate SATA HDD

I first tried install the AMD64 version of Hoary.  It went through the install process fine only to freeze everytime I attempted to login.  I put in my username and password and then a freeze occurs on the splash screen that follows.  On 64 bit version there is no sound.

I then tried the standard 32 bit version.  It freezes at the same place, except we have sound.  It will boot to "Recover Mode" or whatever.  

I don't have any Linux troubleshooting experience so if anyone has any suggestion on how to get this to work I would be greatly appreciative.

Thanks!

Justin

---

### Post by jdarnel2 on 2005-05-07
bump....any ideas?

---

### Post by luca_linux on 2005-05-08
Try to pass acpi=off as kernel parameter at boot to GRUB.

---

### Post by lorap on 2005-05-08
hi friend!
are you sure its an AMD version of ubuntu?

---

### Post by jdarnel2 on 2005-05-08
Tried acpi=off.  No good.

I've tried the x86 and AMD64 editions.  Both fail.

In other news Fedora Core has similar issues for me.  Any other suggestions?

Justin

---

### Post by Kuj0317 on 2005-05-16
Hey, i have the same exact problem.  I was going to start a new theread, but i found this one.  Here's my setup:


Abit IS7-E Motherboard
P4 2.4 ghz
1 gig Giel RAM
Seagate 120 Gig IDE HD
LiteOn CDRW
ATI 9700 Graphics
LeadTek TV Tuner

I noticed that we both have abit baords and Seagate HD's which i think MAY be the cause of our issues.  When booting, does it freeze on ATA100 controller?  I know that mine does, and i have my HD and my CDRom on the same IDE channel, which i believe may be the source of error.  However, i dont have a spare IDE cable to swap it out, so im SOL for trying something else.  Also, you have SATA, is it done via aliasing an IDE Channel in the BIOS?  If so, try messing with that.  If you find anything that works, please post back.  Also, if anybody else has any information on this problem, please post your ideas.  Thank you.

---

### Post by Kuj0317 on 2005-05-17
^bump^

nobody has had a similar experience, or has any ideas as to how to resolve this?

---

### Post by gavd on 2005-05-17
I have the exact same problem. I have tried 32 and 64 bit Ubuntu and am now getting the same problem on 64 bit Kubuntu. It will go to the login screen and then freeze after that. I have no idea what is going on.

Specs:

ABIT KV8
Athlon64 3200
1 Gig Corsair Value Select
GeForce 6800
WD 160GB SATA
Maxtor 200GB SATA
LG DVD ROM
AOpen CD Writer

---

### Post by alastair on 2005-05-17
Might be the X driver.

Boot to "recovery mode" and login.

Then edit the /etc/X11/xorg.conf and change the driver to "vesa" (say) as a test. Then boot up normally and try i.e.

cd /etc/X11
sudo cp -p xorg.conf xorg.conf.bak
sudo vi xorg.conf

Find the line in the "Device" section :

Driver  "<D>" 

where <D> == "ati", "nv" whatever

Change to :

Driver "vesa"

Save and exit.

Boot up as normal :

sudo /sbin/init 2

Any better?

---

### Post by gavd on 2005-05-18
I got round this by typing:

sudo apt-get install nvidia-glx

I guess I had driver problems.

---

