---
title: "Simple Guide for Booting from USB with GRUB?"
date: 2010-11-07
forum: Hardware
---

### Post by bradley002 on 2010-11-07
Hi, I don't understand GRUB or most of linux except for some shell commands. But I am trying to boot Puppy Linux from a USB flash drive, which my BIOS does not seem to recognize. I read the easiest way to make it recognize it is through GRUB, but the guides I have found on it seem to point to Ubuntu-specific processes. Is there an easy step-by-step guide for how to do this on Puppy Linux?

Or is that sort of complicated? I don't necessarily need to run it from a flashdrive, but I thought it would be convenient. Would it be much easier to just create a separate hard drive partition?

---

### Post by oldfred on 2010-11-07
I boot several ISO from one flash drive.

To make puppy work I had to create a separate folder for puppy's kernel & initrd.gz and move lupu-511.sfs to the very top level or / level of my flash drive. 

[http://ubuntuforums.org/showthread.php?t=1600093](http://ubuntuforums.org/showthread.php?t=1600093)

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by bradley002 on 2010-11-07
Thanks...I will check that out. I noticed there are also a lot of suggestions on the actual Puppy installation dialogue in the case that it doesn't boot, for example choosing something besides "MBR" (I can't remember exactly what it said).

So I am not sure if my BIOS isn't configured to boot from a USB or if I need to change something in the Puppy installation. There is nothing in my BIOS boot order that says "removable disk" or anything that indicates a USB drive. It has something called Modular Bay HDD, but I don't think that is USB. Should my first boot option be set to internal hard drive if there is no "removable disk" option?
Thanks

---

### Post by oldfred on 2010-11-07
How old is your system? Is BIOS up to date?

There usually are two places one sets boot order and the other shows bootable devices. Some times you have to select the item in boot order to see the other boot devices.

How do you boot anything other than hard drive?

---

### Post by bradley002 on 2010-11-08
It is a dell Latitude, I bought it used a couple years ago so I am guessing it is 4-5 years old, possibly more. To boot from something other than internal HD I hit F12 during startup and it gives me a list of about 5 things. "Removable Device" isn't one of them.

To change boot order I hit "F2" for setup during startup and then go a couple pages over to boot order. I don't see "removable device" or anything involving USB in that list either.

---

