---
title: "RAID0 mount? help please?"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by groovywombat on 2005-10-17
Alright here's my question?  i just want to be able to mount my existing RAID0 array in breezy.  i don't want to boot from it, I just want it to be useable in Ubuntu.  however i can't even boot into ubuntu when the controller is enabled in the BIOS.  It goes to grub and then when i choose to boot into linux it hangs at the word "boot" it doens't get to uncompressing the kernel.  I've tried booting to different hdds thinking that it was just messing with the device order but that doesn't work either.  This is really the only thing keeping me from switching completely over to ubuntu, but I don't think i can really afford to lose the 160gb of data on that RAID array, and I really don't want to go through the process of backing all that up.  Anyway if someone could please help I would be SO HAPPY.
thanks
The RAID device is a Promise MBFastTrak133 Lite which is built into my Gigabyte 7VAXP Ultra Motherboard, the hdds are IDE.  I'll be trying to boot of a single unpartitioned IDE drive.
thanks again

---

### Post by groovywombat on 2005-10-17
Well I managed to get the computer to boot with the RAID enabled, and the disks show up in fdisk only as 2 different disks, so maybe i just need a driver?  i'm not really sure what to do, if someone could help.

---

### Post by groovywombat on 2005-10-18
Actually in the Device manager the RAID controller shows up so mayeb there is a driver installed and I just need to do something to make the system recognize that the two disks are striped?

---

