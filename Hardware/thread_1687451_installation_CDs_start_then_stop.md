---
title: "installation CDs start then stop"
date: 2011-02-13
forum: Hardware
---

### Post by hdavis on 2011-02-13
[SIZE=3][FONT=Calibri]the problem: when I burn an installation CD from an iso image, then try to boot it in the ubuntu Toshiba laptop machine, it will start to load briefly, then stop. Displays the line:[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]ISOLINUX 4.03 2010-10-22 Copyright (C) 1994-2010 H. Peter Anvin et al[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]and stops. Thankfully, the Ubuntu 10.04 CD booted fine, but that is the only linux product that has so far.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]The DVD/CD rw has worked just fine in the previous windows OS and also works fine in the current ubuntu 10.04. It reads and burns great. [/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I have tried to boot the following in the Ubuntu 10.04 laptop:[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]burned live cd from iso image for ubuntu 10.10(3 attempts),on win7 desktop, Roxio 2010, FAILED[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]burned live cd from iso image for ubuntu 10.04, on win7 desktop, Roxio 2010, SUCCESS[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]burned live cd from iso image for Clonezilla, on win7 desktop, Roxio 2010, FAILED[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]burned live cd from iso image for Ghost for Linux, on win7 desktop, Roxio 2010, FAILED[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]burned live cd from iso image for Ghost for Linux, on Ubuntu 10.04 Brasero, Roxio 2010, FAILED[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Then tried to boot the above on Win7 desktop: Success, so don’t think problem is the burned CDs. And the 10.04 did work….wonder what is different?[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Boot CDs for windows OS targets work fine on ubuntu 10.04 toshiba laptop.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Thanks for your consideration![/FONT][/SIZE]

---

### Post by williamts99 on 2011-02-13
If you already have 10.04 installed, you can just do a distribution upgrade up to 10.10 if that is your goal.

What is the make/model/model-number of the computer?

---

### Post by hdavis on 2011-02-14
Toshiba Satellite M45-S165, 1GB RAM, 80gb HD.
 
Overall goal is to get installation boot cds to work, secondary goal, which requires the first is to get some kind of disk imaging software up and running. Quite happy with 10.04.
 
Funny though, an older Tohsiba did not have this problem and took 10.10 just fine. Have not tried the other installation CDs on the older one because it is in a different part of the country right now. Older Toshiba is a straight *x86* and the M45 is a celeronM if that would make any difference? 
 
Also, played around with Xubuntu which also loaded fine (Liked ubunutu 10.xx better because it was more feature/app rich)
 
*Also just scanned HD for errors and it found some.  Will repair and see if this might be the cause.* 
Thanks for your help William

---

### Post by williamts99 on 2011-02-14
Seems like a very odd problem.  Is there an update to the BIOS or CD-rom drive?  I would look to see if any related issues were fixed.  Try resetting the BIOS settings to default.  Can you boot from a USB memory stick instead of CD using something like unetbootin?

From my searches it seems like there are a lot of these laptops out there running Ubuntu without this issue.  Or maybe we just haven't heard about it yet.  Hard drive errors shouldn't cause any errors booting a CD.

If you like the speed of Xubuntu, or the lighter Lubuntu, you can always install any additional programs that you require/want.

---

### Post by williamts99 on 2011-02-14
Disregard

---

### Post by hdavis on 2011-02-14
Tried the Bios reset. No luck
 
BIOS only gives option for "External Device" boot and not a specific USB boot. Tried the UNetbootin anyway, did not work in laptop. Checked it on desktop (using Clonezilla) and worked fine. 
 
Will be trying new HD in a few days when it arrives since i ordered a few days ago. I know you said, and I concur, should not have any effect on CD boot, but, at this point, gotta reach for the long shots.
 
*Trying to think through this logically...factory "pressed" cd's boot fine, i.e. windows installation cds. Also, burned copies of windows installation cds work fine. Boot CD created by True Image 2011 works fine.*
 
*Since the DVD/CD RW drive works fine reading and writing in Ubuntu 10.04 or WinXP sp3, and boots the above CDs just fine, i can only conclude it is not a DVD/CD drive or BIOS problem. None of these were created using iso image burns.*
 
*So where does that leave us? What remains is the burned iso images (which boot fine in the desktop). All these appear to use isolinux (ubuntu 10.10, clonezilla, ghost for linux). *
 
*Hypothesis: Some variant of isolinux (or whatever initially loads) is not compatible with the toshiba M45-S165 BIOS/system. Is there a different older version of isolinux (or whatever initially loads) on earlier versions of ubuntu that do work in the toshiba (i.e. ubuntu 10.04, xubuntu 10.04)? And perhaps a newer version is present on the Clonezilla, Ubuntu 10,.10, and Ghost for Linux that does not work on the toshiba?*
 
Thanks again for the help

---

### Post by williamts99 on 2011-02-15
Yes, it seems that there is something with the bootloader.  Might want to post on the mailing list for syslinux, they will know a whole lot more about it. Or if you have a floppy drive, you can try to load up from the smartbootmananger.  Another thing I have used is PLOP boot manager to boot USB on computers that don't normally boot from USB. I boot that from CD, and then load up the Ubuntu install from USB.
[http://syslinux.zytor.com/wiki/index.php/ISOLINUX](http://syslinux.zytor.com/wiki/index.php/ISOLINUX)
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

---

### Post by hdavis on 2011-02-15
Wow, whole new universe out here in Ubuntu land! Will pursue those.
 
Don't know the protocol for closing a thread, but i think we have determined this is not an ubuntu problem.  I respectfully suggest we close.  Your suggestions will get me where I need to be.
 
Many thanks to you!

---

### Post by williamts99 on 2011-02-15
You can mark the thread as 'solved' using the thread tools above your first post on this page.

But otherwise, people(us) will just stop posting, and eventually it will be in the archives :)

---

### Post by hdavis on 2011-02-16
Will do that... h

---

