---
title: "New SATA hard disk not recognized"
date: 2012-09-08
forum: Hardware
---

### Post by meanmrmustard on 2012-09-08
I recently added a new SATA disk to my present installation for backup purposes. It is a Seagate 3 TB internal drive.
It has a GPT partition table and was formatted as ext 4.
This is the same process I did when installing two other 3 TB drives in this machine months ago and they are still working flawlessly - the only difference is they are both external drives, also Seagates.

The first time I tried to format it, (using gparted) it looked to be successful but the Ubuntu disk utility showed no file system type. The second time it got formatted correctly and was recognized normally.

I then ran luckybackup to copy over 2 Tb of files. It ran normally at first, but suddenly the machine froze after a few minutes of copying files. There was no noise from the drive and although it's not recognized, it does feel warm to the touch after the system is up and running.

The screen went black and would not respond to any key presses. 
Tried switching to tty1 with  ctrl> alt> F1 and also tried ctrl> alt> delete, neither combo produced a response.
After rebooting, the drive was recognized and once again I started the backup program and again the machine froze up, the screen went black and nothing but killing it with the power button had any affect.

Rebooting once again I found the drive not recognized in either the BIOS or from within the system. sudo lshw did not show the drive nor did Gparted although the other two 3 TB drives connected to the machine show up as expected.

Also it began a long delay while attempting to detect the new disk during the boot process before finally starting up.
After disconnecting the new drive the system booted normally but re-connecting the new disk I got the same long delay before finally starting up the xubuntu install (10.04) with no trace of the new disk.
Also tried two other SATA cables with no success and also connected the cables to the other unused SATA port (onboard).

I tried live cd's (Linux Mint and Ubuntu) but it did not show up under either of these either.


Viewing the logs, I see nothing suspicious - no indication of a problem.

Dmessage shows the other four hard drives as does the mount command and "sudo fdisk -l" also shows sda, sdb, sdc and sde (all SATA disks)but no sign of the new Seagate disk.

As I write this I thought of one thing I haven't tried - booting to the Gparted live disk which I will try later when I have the time but I think the results a likely to be the same.

Any input and/or suggestions would be greatly appreciated.
In the meantime I'll also try the Seagate's Seatools to check the disk itself for problems.
I'll also attempt to connect it to another machine if there's a SATA port available - can't remember whether or not there is at the moment.

Beyond what I've already tried, I'm out of ideas and my friend google has not been much help.

---

### Post by oldfred on 2012-09-08
Someone posted this, if you happen to have Asrock with Asmedia:
So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

My system can have different BIOS settings for groups of SATA ports. Are settings consistent and AHCI for all ports?

---

### Post by meanmrmustard on 2012-09-08
> **oldfred said:**
> Someone posted this, if you happen to have Asrock with Asmedia:
So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

My system can have different BIOS settings for groups of SATA ports. Are settings consistent and AHCI for all ports?

This mainboard is an Asus M4A88TD-V EVO/USB3. Settings have always been IDE but I tried AHCI setting earlier (all ports change to one or the other) doesn't make a difference.

I've tried Gparted live disc - it doesn't see the drive. 
I'm beginning to think the drive has an electrical problem. It spins but that's it.
I'm about to see if it will show up in another machine, if not I think it's RMA time.

---

### Post by meanmrmustard on 2012-09-09
Update:

Connected the drive to another machine and after an hour it was still hanging as it tried to detect hard drives.

Time to try a replacement.:mad:

---

