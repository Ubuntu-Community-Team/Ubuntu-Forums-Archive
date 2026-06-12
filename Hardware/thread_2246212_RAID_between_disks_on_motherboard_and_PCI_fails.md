---
title: "RAID between disks on motherboard and PCI fails"
date: 2014-09-29
forum: Hardware
---

### Post by eotakos on 2014-09-29
Hello everyone,

I am trying to put together a RAID 5 with three disks. This is a low cost project of mine, so I'm using an old motherboard that has only 2 sata ports. For the 3rd one, I used a PCI card (with an extra 2 ports, one of them is unused). 

So I have partitions of the same size on all 3 disks to use for the raid, but when I construct the raid, the system freezes. I restart, I try to put the raid together again, the system freezes again. We're talking about kernel panic of the worst kind, that's not even reported in the kernel logs :)

Anyone has any experience on this? Is what I'm trying to do even possible? or I'm just wasting my time and I should go buy a motherboard with all the ports I want?

My first thought is the speed of read and write between the drives is very different, and this is what the system doesn't like. But speed is not my concern at all in this project (the speed of the slowest drive would do just fine), so is there any software option to limit the speed of the faster drives that are connected to the motherboard?

Any input will be appreciated!

Thanks in advance,
Pana

---

### Post by tgalati4 on 2014-09-29
Try logging in using ssh from another computer and hopefully system errors will get thrown to the console.  Otherwise check /var/log/syslog for any error messages.  But yes, RAID requires a high-performance SATA setup.  A timing mismatch between the drives could cause a problem.  It could also be a bad PSU.  When you have extra cards and 3 spinners, your PSU may not be able to provide enough current.  This condition results in a voltage drop that causes the motherboard to freeze.

For your hardware, I would experiment with a single drive for boot and use the other 2 drives in a RAID1 mirror for your data.

---

### Post by eotakos on 2014-09-29
Thanks for the input!

So I tried doing everything via ssh... I didn't get much info :
"mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md127 started."
and then nothing. Both the remote connection and the local logins died... frozen screens.

As regards your setup suggestion, I planned to have 3 drives dedicated to the RAID 5... So in total they are 4 spinners, one of them with the OS on it (12.04 32bit). But I specifically bought a new 450w power supply to make sure the voltage wouldn't be an issue. Do you think it could still be?

I guess I'm not avoiding buying a new motherboard to do what I want.

---

### Post by Forbees on 2014-09-29
on my setup i'm using a 3 drive RAID5 with a 500 watt PSU... used to be a spinning drive for the OS, but now it's an SSD, so i feel like you having only 50 watts less than me shouldn't be an issue..

---

### Post by Vladlenin5000 on 2014-09-29
There are many things to consider for a PSU than just wattage. With 3-4 spinners you need a PSU with "robust" 12V rails (hey, I'm not an electrical engineer).
Assuming the PSU isn't the problem the issue of that configuration itself remains. Building a RAID with disks managed by different chips is more often than not a huge PITA, even if both are onboard. And also more often than not, cheap add-on cards similar to yours don't "play nice" with many motherboards' chipsets, RAID or no RAID.

I once had one with a fair share of freezes and other annoyances in an Intel based PC; an AMD based PC with the same card couldn't even boot.

---

### Post by tgalati4 on 2014-09-29
450 watts should be sufficient.  I would only attempt RAID using a common controller for all disks in the RAID.  Anything else is just asking for problems.

---

### Post by Michael_McKenney on 2014-09-30
Size of a power supply does not really matter.  It is how the wattage is distributed across rails.  My PC Power and Cooling 1000W power supply is a single rail design.  Capable of 100W @ 12V.  I bought it for my server grade hardware.  I have 4 SAS drives, 6970 graphics adapter capable of 380W of power usage, and dual Xeons or Opterons.   I have seen lower end power supplies be 2-3 rails that have issues with how their loads are split.   With 3 or more hard drives, I would recommend no less than a 650W.  If you have a higher end video adapter 750W.  You also want to determine what else is on your computer's circuit.   Sharing with other higher wattage devices like a refrigerator, windows A/C or HDTVs can cause issues of power drops, when they turn on and off.  I installed a two 20A @ 120V circuits for my workstation and devices.  One for the 1000W power supply and one for my monitor, printers, etc.

---

