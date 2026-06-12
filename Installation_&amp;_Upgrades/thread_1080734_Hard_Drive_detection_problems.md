---
title: "Hard Drive detection problems"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by joeythebean on 2009-02-25
Evening everyone. I'm really struggling to get Ubuntu installed on my computer. Its a second hand home built desktop.

There seems to be no problem running Ubuntu from the CD but when I try to install it always fails at the HD partitioning stage.

The error is:
"Failed to create a swap space
The creation of a swap space in partition #5 of SCS15 (0,0,0) (sda) failed"

I've been looking around on forums for a few days now but can't find a solution anywhere. GParted can't detect the HD either and I'm getting no response after pressing F4 on start up to access RAID setting, so it seems to be that there aren't any drivers for the HD. So I look for drivers for a Seagate internal 120GB and find that they're nowhere, and how would I install them anyway as I don't have an OS?

Seriously lost and seriously new to linux so help would be much appreciated.

I've tried updates for GParted, entering "acpi = force irqpoll" on installation, and I've even tried installing XP which again fails at the "examining hard disk" stage.

Thanks in advance.
Joe

---

### Post by cariboo on 2009-02-25
Have  you tried setting the patitions manually?

Jim

---

### Post by joeythebean on 2009-02-25
I have.

10000MB for /boot
3000MB for swap
remainder for root

Cheers for looking

---

### Post by absolutezero1287 on 2009-02-25
If you have RAID shoudn't your BIOS also be configured to properly use RAID?

---

### Post by logos34 on 2009-02-25
you only have one disk?  Does the Bios recognize it?

---

### Post by joeythebean on 2009-02-25
I got the computer off my brother as a present but he didn't have a computer delivered in time to swap his data so he removed 3 of his 4 HDs. It is possible that I haven't set up RAID correctly, but I'm not quite sure what I'm doing with it. I tried accessing the RAID menu on start up but with no luck. No response on F4 press and it says 
"Channel 1: Driver not found
Channel 2: Driver not found"
or something similar. 
Struggling to use the computer I'm trying to fix with a 15min boot time. :-P 

What do I need to do in BIOS to set up RAID correctly? I changed one setting to PCI/s card or something but that didn't help.

And yes BIO's recognises the HD. Tells me its a ATA ST3120026AS. I got that from somewhere, maybe not BIOS.

---

### Post by absolutezero1287 on 2009-02-26
Well, if you can't configure your RAID controller then check your boot order and make sure that only one hard drive shows up. Make sure that hard drive is set to boot. Then GRUB should take care of the rest.

---

### Post by joeythebean on 2009-02-28
Hey all. Still no luck sadly.
Tried the advice but there's no progress. Only one drive is being recognised (I've only got one) in BIOS and its set to boot.
Not sure what GRUB is but its not taking care of the rest. :(

I have noticed the that the hard drive is sometimes being recognised by Ubuntu in the 'Places' drop down menu, (only after a failed and cancelled install, not after selection of running without changes at the cd boot menu).

Is the hard drive meant to be read as : vSCS15 (0,0,0) ?? (Pointing out the zeros in the brackets.)

I've pursued a driver for the motherboard (LANPARTY 865PE) but not quite sure what I'm looking for.
Is it looking like I just need a new hard drive?

Thanks again

---

### Post by joeythebean on 2009-03-31
Couldn't find a solution so got myself a new HardDrive. 

Cheers for help anywho

---

