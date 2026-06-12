---
title: "Fried hard disks"
date: 2013-05-17
forum: Hardware
---

### Post by heWhoWearsAshes on 2013-05-17
Hey everybody,

I received a new power supply and vga in the mail today. When done installing them, I powered on my comp and it said "insert bootable media". I checked everything out, and it turned out I had the sata power cable plugged into the wrong hole.... Google says that when there's electrical damage, it's usually not inside the hard disk case, which makes me imagine that I can still salvage it. How would I know that the control board, and not the platters themselves, is damaged? I didn't find any smoke when I powered on, but I can't hear any sounds from the hard disk when I power it on. 

I need a better opinion than what google has to offer! Advice please!

---

### Post by tgalati4 on 2013-05-17
There are multiple SATA ports.  Try each one.  Get a USB enclosure and insert the disk and try using it as an external drive.  If you can't feel the drive spinning up or hear clicking, then the drive electronics are probably toast.  You can try to remove a controller card from another identical disk.  This is not always successful, because modern drives use digital trim functions that are specific to each platter assembly and controller card, so swapping cards way not work reliably.  But if a drive has important data on it, then it's worth a try.

Use a magnifying glass and see if you can detect any burned resistors or diodes on the control card.

Take a known, working, SATA drive and test all of your SATA ports to make sure they are working.  If the SATA ports are burned on the motherboard, then you might need a new motherboard.

---

### Post by heWhoWearsAshes on 2013-05-18
Thanks man. I have a spare, and I plugged it in and it spins up, so hopefully no damage to the mobo. Since it's damaged, it's gonna be the donor. I have to get work stuff out of one I broke yesterday.

---

### Post by MartyBuntu on 2013-05-18
You probably fried the controller board on the hard drive.

Is it even possible to plug the SATA power connector *anywhere else?*
:shock:

---

