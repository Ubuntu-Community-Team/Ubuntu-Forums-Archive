---
title: "Sata hard drive not found during boot"
date: 2010-10-27
forum: Hardware
---

### Post by DaSaint on 2010-10-27
**Problem:**
Installed Ubuntu 10.10 and everything looked great.
After a reboot all of a sudden my system became super slow to boot and ended up in a prompt that said initramfs.
I tried booting in recovery mode and that told me:
ata3: softreset failed (device not ready) 

I had just gotten my computer updated (new mainboard, processor and graphics card.)

I have three hard drives, the two main ones connected with one IDE cable, one Sata drive and one dvd writer connected trough SATA.

The dvd writer got recognised, just not the Sata drive.

Even in the BIOS  the drive was not seen any-more.

I was eventually able to boot by disabling the onboard Sata controller in the Bios. But then Ubuntu showed a message it was unable to mount my drive.
It was also not found by Gparted.

Then after a reboot the problem magically solved itself only to represent itself the next day.

**Attempted to resolve problem:**
I tried messing with the BIOS settings, enabling and disabling the on board Sata controller. Changing the Raid settings from IDE, to RAID to AHCI.
No luck.

I tried adding  -- pci=nomsi to the boot parameters after “quit splash” 
I tried checking the jumpers on my maxtor drive for a “force 150” setting but it was already a 150 drive.

I tried plugging the Sata cable of the hard drive into another port. Even tried changing the cables between my Hard drive and my dvd writer. 

**Solution:** 
It turned out the solution was a really stupid one. I saw in the manual of my mainboard that a SATA cable cannot be bent more then 90°.
My cable was quite twisty and bendy.
I took it out and made it go a lot straighter and with gentle curves.
Problem seems to be solved.
Fingers crossed :)

---

### Post by DaSaint on 2010-10-28
Well, I guess I cried victory to soon.
Another reboot and the problem is back.

I've now tried flashing the Bios with the latest version. Will now after a reboot if that worked.

I had unplugged the Sata cable to be able to work a little faster. Keeping it connected caused my system to be super slow from the second it started to boot.

Plugging my Sata cable back in causes it to work the first time, but after a reboot the hard drive will not be detected again and my system super slow.

---

### Post by DaSaint on 2010-10-29
Well I finally got to the solution (or a solution).

I ended up checking everything related to that drive.
I changed the Sata cable, the power cable, put it on another sata connector and changed the sata settings in the Bios to every possible possibility (IDE, RAID, AHCI) also disabled the onboard Sata driver.

In the end I had to conclude it had to be the drive that was the problem.
It was a Maxtor Diamondmax 10. It's one of the first sata drives from Maxtor. It was a 150 version so no jumper to force 150.

The problem was already visible at the first bootscreen so it was not an OS problem.
I run Ubuntu 10.10 and have Windows XP on a dusty partition somewhere.

I ended up changing the hard drive with a Western Digital Caviar Blue 500Gb 300Sata drive.

This one seems to be working perfectly. I only powerd down once but the Western Digital kept on going where my Maxtor gave up.

Now I never had this problem with my old motherboard (Gigabyte GA-K8VT800 Pro)
There can be two conclusions. Either my disk was getting old and my previous Motherboard did not really have a problem with that but my new one did.

Or the hard drive is still in good shape but there is some kind of funky compatibility issue between my new MSI (785GM-E51) and my old Maxtor.

I guess I'll never know. The maxtor has been retired. Anyone want it?

---

