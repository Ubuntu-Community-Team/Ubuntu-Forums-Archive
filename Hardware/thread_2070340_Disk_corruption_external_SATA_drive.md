---
title: "Disk corruption external SATA drive"
date: 2012-10-12
forum: Hardware
---

### Post by Richard J Moore on 2012-10-12
I'd appreciate an opinion on this scenario as to whether this is a driver bug and whether it's known. I'm running these tests on 10.01.4 and 12.04.1 and the results are the same. Here's what I first noticed:

I have a new 640GB 2.5" SATA drive attached via a Supertop chipset SATA-USB bridge. 
Scenario 1) Create a primary partition under Linux using fdisk - save the partition data. Unplug the drive, re-attach it. fdisk now shows a virgin  partition record.
Scenario 2) Create the partition table under Windows. Unplug and attached the device to Linux. Use fdisk to view the partition table. It appears as setup as under windows. Now format one of the partitions using mkfs.ext4. fdisk now shows a virgin partition table. It has completely vanished. Scenario 3) Use Windows to create an NTFS partition. Copy a file to the partition under windows. Attach the device to a linux system. It mounts and the windows file is readble. Next create another partition. Cleanly removed the device and reattach. The NTFS partition has gone.

Further investigation shows that the CWB header is being written to the disk in the place whether the data should go. I see the USBC signature where the data should be.

So to prove this I traced the USB packets using wireshark while using hexedit to write to sector 0 offset 0, 40 bytes of 11x.
I see the packet to write my data, actually 1KB is written. My data begins at +18x into the user data area. There's no USBC characters in that packet.
When I use hexedit a second time I see the USBC command packet written to sector 0 and my data written to sector 1.

If I write to sector 2, then sectors 2 and 3 get globbered and sector 3 has the data I intended for sector 2. If I edit 2 consequtive sectors at once the second sector goes to a completely different disk location. 

Now compare the with an external IDE drive pluged into a USB bridge.

I see them same type of data packet from wireshark. My data at +18 into the data buffer. IDE seems to want to write to the disk in 4K chunks (not relevant I think). This time data stays where I put it. And there are no USBC strings on the disk - at least none that I could see.

I'm hoping there's a simple config work-around to this. 

Dmesg shows the the usb device is frequently reset, I think this is a consequence of the mishandled packet rather than the cause. I've also tried a second USB caddy. It gives the same results. In both cases the Supertop chip set is being used.  

Any ideas?

Richard.

---

### Post by ahallubuntu on 2012-10-12
With Linux, I've found that sometimes its easier to solve certain problems by getting different hardware that works better with Linux than to spend hours and hours trying to tweak something (having been down that road more than a few times, too.).

So, I'd suggest getting a different USB bridge/different chipset that does not have this issue.  I assume you've already googled for info about this particular device and any known kernel issues with it?  If you try a different chipset and have the same issue, then maybe it's an issue of the USB chipset on the computer itself.

I have several SATA-USB bridges that have worked fine with Windows and Linux, and some of them are cheap.  I have bought a couple of cheap USB-2.5" SATA enclosures for $4 USD on sale and they work fine, even if not always the best performance.  For example, I recently got a 1TB 2.5" WD laptop drive and attached it to at least on USB bridge and had no issues at all, though I didn't go back and forth quite the way you have between NTFS and ext4 stuff.

---

### Post by Richard J Moore on 2012-10-12
yeah, that's my next port of call. I have on order a different caddy, with, I hope a different chip set.

---

### Post by Richard J Moore on 2012-10-17
A new external SATA caddy arrived today and turns out to have the Super Top chip set - and same problem. Can anyone recommend a make that uses something other than Super Top?

Richard

---

### Post by Richard J Moore on 2012-10-18
This seems to be a regression from Oneric. No problems partitioning and formatting under Oneric. If I mount and unmount one of the partitions on Pangolin then the partition's superblock is trashed (according to the message). Not tried with Oneric desktop. 

>> I have now tried with Quantal server and desktop. The problem appears on the Desktop version but not on the Server. 

Richard

---

