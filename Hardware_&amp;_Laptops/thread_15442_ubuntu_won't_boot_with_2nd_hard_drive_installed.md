---
title: "ubuntu won't boot with 2nd hard drive installed"
date: 2005-02-14
forum: Hardware &amp; Laptops
---

### Post by thewolf on 2005-02-14
I have Ubuntu (Warty) installed and running on a 3Gb drive.  Now I want to add a second drive which is a 20Gb Fujitsu MPF3204AT.  As soon as I plug it in and boot, the boot goes much slower, and it eventually seems to stop at something about LVM.

The new drive is recognized correctly in the bios, and it currently has no partitions.  Ubuntu won't boot so I can run fdisk, so I'm not sure what else to try.  Sometimes (depending on bios settings) I get errors about dma timeouts on the drive, otherwise, no error messages.

Help!!

---

### Post by thewolf on 2005-02-15
Anyone?

It's jumpered as slave and plugged in as slave on ide0, so it should be showing up as hdb.  The drive was previously in a working Windows machine, so I know the drive is ok.

How can I get it to boot so I can at least get to fdisk?

---

### Post by thewolf on 2005-02-16
This is driving me CRAZY!

I downloaded a diagnostic utility from Fujitsu, put it on a bootable floppy, and tested the hard drive for bad sectors.  It passed with flying colours, so then I used the utility to completed reset the drive by writing empty data to the entire disc including the partition table, boot record, etc.

Then I booted back into Linux and guess what--it booted!  Woohoo!!

So I created a partition (using fdisk in Ubuntu), that used the whole drive, and had no problems or errors.  Then I ran mke2fs -j /dev/hdb1 and created the file system, also with no problems or errors.  I edited fstab to mount hdb1 at media/data and rebooted.

Guess what--IT WON'T BOOT!!!  What in the wide, wide, world is the deal with this thing?!?  Somebody give me some advice!

Presumably I can use the Fujitsu utility to reinitialise the drive, and then I'll be able to get back into linux, but I don't know what to do then.  I'm a complete newbie with linux, so I don't know what utilities might help me diagnose the problem.

Any help would be GREATLY appreciated.

---

### Post by thewolf on 2005-02-17
I've confirmed that if I completely erase the drive with the Fujitsu utility, it will boot fine, but as soon as I prepare it in linux, it won't boot the next time I power down.

This time I partitioned it, made the filesystem, and mounted it--all with no problems.  The drive showed correctly, with the correct capacity, and the mount went flawlessly.  As soon as I tried a restart, it will no longer boot.

Is it an issue with the timing of when it recognizes the drive during bootup?  Something in the kernel?  Should I recompile the kernel once I have it working and before I shut down?  There has to be someone with some ideas  [-o<

---

### Post by xinel on 2005-02-18
hello thewolf

have you set the drive to auto mount? see below


/dev/hdb1	/home		reiserfs	auto	0	0

- xinel

---

### Post by thewolf on 2005-02-18
You mean in fstab?  Yes, it's set to mount to /media/data.

But the problem is not that the drive doesn't show up--it's that once it's partitioned and a filesystem is created, ubuntu won't even boot.  I can't even get to the desktop.  It just hangs at the line about loading raid controllers, and the drive light stays on continuously.

If I reinitialise the drive from a boot floppy (and therefore wipe out the filesystem and partition), it's fine and ubuntu boots without difficulty.  As soon as I put a partition and filesystem on the drive, it works until I have to shut the computer down, and then it won't boot.

---

### Post by thewolf on 2005-02-21
Is there no linux guru out there who can share some wisdom about this?

I was wondering whether it might be a problem with grub, but doesn't grub just get the ball rolling so to speak?  Once I've got a partition on the problem drive, I get fairly far in the in boot process before it hangs.

I just don't get it.  Why would ubuntu be happy with the drive as long as it's unformatted and has no partitions, but can't boot as soon as you add a partition (and add the partition within ubuntu itself no less)?? ](*,)

---

