---
title: "New SATA hard disk not being detected"
date: 2011-02-08
forum: Hardware
---

### Post by Dragonbite on 2011-02-08
All of my computers are second-hand (except 1 laptop but it doesn't count) and I see in my Dell 4600 there are 2 SATA connectors on the motherboard.  I picked up a 250 GB SATA hard disk and cables recently and tried plugging it in but the system doesn't see it.

I even disconnected all other disks to make sure there wasn't a conflict (master/slave) issue going on but the system still does not see it.  The disk is vibrating so I assume it is getting juice and is spinning.

Is there a setting or something I have to do to tell the system to access the SATA? Do I have to look at RAID settings if there is only 1 SATA disk?  Can I not have a SATA disk and an ATA disk plugged in at the same time?

I want to try and determine if the disk is bad, or is it PEBKAC!  Any advice is appreciated.

---

### Post by cascade9 on 2011-02-08
Have you checked your BIOS settings? If the SATA ports are turned offin the BIOS, seeing the drive is pretty hard ;)

---

### Post by P4man on 2011-02-08
Are you sure its not being detected? Can you post the output of

```
sudo fdisk -l
```

If it doesnt show up there, does it show up in the BIOS? As mentioned above, maybe the sata controller is disabled in the BIOS.

---

### Post by Dragonbite on 2011-02-08
Where is the SATA controller typically turned on and off in the BIOS?

I see in the Hard Disk listing it lists SATA Master and SATA Slave but it doesn't give me any options other than "n/a"

fdisk -l shows me nothing.  I didn't try it with sudo so I'll give that a try.

---

### Post by P4man on 2011-02-08
well, so the drive isnt showing up in the bios, no way it will turn up in ubuntu (or windows). Dont bother with fdisk.

SATA settings would be usually be in "integrated peripherals" or something. What bios do you have?

---

### Post by cascade9 on 2011-02-08
P4man is right, its normally under "Intergrated Peripherals", but not always. It depends on yoru BIOS vendor, BIOS version, and what hardware is in the system. 

I did have a quick look and found this, maybe it will help- 

[http://en.community.dell.com/support-forums/desktop/f/3514/t/19242453.aspx](http://en.community.dell.com/support-forums/desktop/f/3514/t/19242453.aspx)

Thats for a 4600i, but it might be close enough to give you a hint. About 3/4 of the way down that page, somebody has posted a pic of the BIOS screen with some of the HDD options up. 

Hopefully just turning the SATA drives 'on' will work. ;)

---

### Post by Dragonbite on 2011-02-08
I'll have to look when I am at home.  The system is a Dell Dimension 4600, Pentium 4 at 2.4 GHz.

It also been suggested that make sure the SATA ports aren't configured as RAID.

---

### Post by Dragonbite on 2011-02-08
Could it be the SATA is not getting enough power?  I got an adapter from the power supply for the SATA but I don't know if that will be powerful enough or not (don't know what, if any, difference of power draw the drive has).

It is getting some power, but I can't tell if it is enough juice.

---

### Post by P4man on 2011-02-08
> Could it be the SATA is not getting enough power?
Highly unlikely. Probably sata is just disabled.

---

### Post by Dragonbite on 2011-02-08
Thanks for all of your help.  It was indeed having to be turned on in the BIOS.

After I was able to verify it was detectable, I switched back to the ATA and tried booting up. It failed because it was looking for SATA drives first. I returned to the BIOS and turned the SATA drive off. 'Lo and behold, it booted up properly.

Now comes getting time on the machine to partition and use clonezilla to copy the disk over to the new one!

---

