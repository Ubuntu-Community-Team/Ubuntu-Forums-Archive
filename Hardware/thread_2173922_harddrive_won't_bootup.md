---
title: "harddrive won't bootup"
date: 2013-09-11
forum: Hardware
---

### Post by gleplae on 2013-09-11
I have installed ubuntu 12.04 on a sata hard drive and have been using ubuntu fine for a couple of month now. I wanted to install a second ide hardrive which has windows 7 installed on it. When I connect the ide drive to the system I can detect both drives in the bios but when I go over to the boot menu in bios the sata drive containing ubuntu is not listed in the boot menu.

---

### Post by Bashing-om on 2013-09-11
gleplae;
Let us make sure we are on the same page.
Bios; Does have options in the "setup" pages to set the device boot priority; this option is not to be understood as the same as an operating system boot menu.

One sets in bios the boot device priorities so that bios knows where the boot code is located on the hard drive(s), so the boot code is found.

Bios hands off to the boot code (that sets up the boot menu) and then the hand off is from the boot code to load the selected operating system.

Is what you are referring to is an inability of the boot code to boot the desired operating system ? 

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by gleplae on 2013-09-12
I am referring to the device boot priority in the bios setup pages the harddrrive which contains ubuntu is not listed in bios boot priority menu when the ide harddrive is plugged in but if I unplug ide drive the ubuntu drive appears as a boot option.

---

### Post by Bashing-om on 2013-09-12
gleplae; Hey..

All I can think of is the bus controller is unhappy ...
As you only have the one IDE drive have you checked to insure the "cable select mode" pinning is set to "master" ?? Maybe with a SATA drive also installed perhaps one of the of the three modes need to be (re-)set ?? master - slave - cable select

Nother thought is no matter the location of the drives in respect to cables, maybe the sata gets recognized long before the IDE drive .. and when the IDE drive is picked up .. Bios is going bonkers as the sata drive has already been assigned to the spot that the IDE drive is set to take ??


[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by gleplae on 2013-09-12
The sata drive I have is a western digital WD1600AVJS and it says master slave jumpers not required for sata, the ide drive jumpers are set to cable select. Does it matter which sata port I have the sata drive plugged into?

---

### Post by Bashing-om on 2013-09-12
gleplae; Well//
Sata; correct that there is no pinning..
IDE: I would also think that "cable select" is appropriate - maybe if chained with other IDE drives(??) might try changing the pinning to a different pinning and see if bios will list the drive in the "setup: page.

You may swap the sata ports around ... but I doubt that will make a difference. If you do switch the ports, will have to remap the drives in the operating system. I did that a while back [sata drives]and it took me ages to figure out why I could not boot (triple booting) properly.

[INDENT][INDENT]all I can think of presently
[/INDENT][/INDENT]

---

### Post by varunendra on 2013-09-13
> **gleplae said:**
> I am referring to the device boot priority in the bios setup pages the harddrrive which contains ubuntu is not listed in bios boot priority menu when the ide harddrive is plugged in but if I unplug ide drive the ubuntu drive appears as a boot option.

So both the drives are listed in BIOS setup's information page, but not in the Boot Device priority page?

Is there an expandable **Hard Disks** (or Hard Drives, or similar) menu in the same Boot priority setup page? If yes, are both drives listed in it?

Many BIOS setups can only boot the drive that is listed at the top of the "Hard disks" menu. If yours is a similar one, you can change the listing by putting the SATA drive on top (by pressing +/- when in the "Hard Disks" menu).

This is kinda crippled functionality, but that's how many BIOS setups are..

If the above doesn't apply to your BIOS, it may help if you post a screenshot of the "Boot Device priority" setting page, also a screenshot of a "Quick boot device selection menu" if yours has one.

---

