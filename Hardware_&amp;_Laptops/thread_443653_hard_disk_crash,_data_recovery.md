---
title: "hard disk crash, data recovery"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by ittiam on 2007-05-14
All of the sudden my hard disk crashed. Whenever i try booting the system says Hard disk not detected. Anyways i have got a new hard disk but i need to recover data from the old one. I have installed feisty in it along with win xp home. Is there anyway to recover the data using the live cd along with special boot parameters. when i type "rescue acpi=off" to boot the system keeps running some tests for a long time and some times it starts booting but it invariably ends up in a kernel panic and asks me specify the value for root in the boot option. 

Any help will be greatly appreciated as I have lots of important data in the old disk

---

### Post by ghostboy on 2007-05-14
> **ittiam said:**
> All of the sudden my hard disk crashed. Whenever i try booting the system says Hard disk not detected. Anyways i have got a new hard disk but i need to recover data from the old one. I have installed feisty in it along with win xp home. Is there anyway to recover the data using the live cd along with special boot parameters. when i type "rescue acpi=off" to boot the system keeps running some tests for a long time and some times it starts booting but it invariably ends up in a kernel panic and asks me specify the value for root in the boot option. 
 
Any help will be greatly appreciated as I have lots of important data in the old disk
 
I would try a LiveCD version of Knoppix 5.1. By using Knoppix and booting to the CD you will be able to see your hard drive that crashed, rescue the files, and put them onto your new system. I use Knoppix in all of my data recovery. Hope this helps.

---

### Post by ittiam on 2007-05-15
I guess it is a physical damage to the hard drive & there is no way to recover data! :(

---

### Post by ghostboy on 2007-05-15
> **ittiam said:**
> I guess it is a physical damage to the hard drive & there is no way to recover data! :(
 
 
Sorry to hear that. What did you do to the HD? ](*,)

---

### Post by yey365 on 2007-05-15
If the old disk is still in the system and attached to an IDE ribbon, check the BIOS to see if it is seen there.  If it is, the OS should see the disk and try to mount it.  I don't see the need for a live distro if this is the case as you will have the tools it contains to perform recovery wither by drag and drop or CLI.

If however you have a dead system, then Knoppix is good, but don't forget the trust Ubuntu live cd.

Hope this helps.

Jim

---

### Post by ittiam on 2007-05-15
I did not do anything to the hard disk. Suddenly i heard some tick sounds and the entire system froze! Knoppix is not even detecting the hard drive...nor is it seen from the bios! Will it be of any help if connect the hard disk externally through a connector to another system?

---

### Post by yey365 on 2007-05-15
You could try that if you have spare system or a usb caddy.  The ticking noise you heard is indicative of a dying hard drive but you might get lucky.

---

### Post by ittiam on 2007-05-15
what is a caddy?

---

### Post by Detonate on 2007-05-15
Here's a trick I have used successfully on bad hard disks, but I warn you it does not always work.  It depends on whether the crash was caused by an actual physical problem, or a failed component on the HD's circuit board.  

Search Ebay for an identical HD.  It must be exactly the same make, model, size, etc.  Buy it.  Remove the circuit board from both disks and swap them.  Then reinstall your disk and give it a chance.  In my experience this works about 70% of the time.  But if the info on the disk is important, its worth a shot.  If the info is really important, (worth a lot of money) there are places that will try to do data recovery.  Sometimes they even go so far as to actually remove the disks from the drive and install them in another drive.  Depends on what it's worth to you.

---

### Post by yey365 on 2007-05-16
Caddy= external usb enclosure.

If the data on the drive is critical, and the logic board replacement route is not viable, there have been some reports that freezing the hard drive overnight and then attaching it to the system may allow you to power it up once allowing recovery of data.

In my experience though, if the drive crashed then the read/write heads will have gouged in to the disk platter and any subsequent recovery would have to be performed by a specialist firm.  This would cost you a fair bit of money.

Regards,

Jim

---

