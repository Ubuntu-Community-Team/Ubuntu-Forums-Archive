---
title: "ubuntu on a portable HDD?"
date: 2008-11-26
forum: General Help
---

### Post by fillintheblank on 2008-11-26
Just a thought, is it possible to install and run ubuntu on say a portable hard drive?

---

### Post by decard_pain on 2008-11-26
yes it should be possable.
you may need to unplug you main hard drive to make sure it installs grub to the external drive.
only problem i see with doing this is your external drive will not have the same number on another system
e.g

sd1 sd2 sd3 or hd1 hd2 hd3.

to get this to work you will need to edit your menu.lst on the external drive
/boot/grub/menu.lst

so it points to all the possible drive number combos..
i'm not sure exactly how you would do this so you may have to do a little research

---

### Post by Radioman991 on 2008-11-26
Yes it is possible.  Do it every day.  Company laptop has Windows on an encrypted internal HDD.

I removed the hard drive, so as not to risk killing it...which I DID the first time I tried this!

Set USB as first boot device in BIOS...and installed Ubuntu to a 100 Gig LACIE USB drive.

Popped the Windows drive back in, and boot to Windows for work..When day is done, and I want to use Ubuntu, shut down, plug in the USB drive, turn on and POOF  Ubuntu laptop.

---

