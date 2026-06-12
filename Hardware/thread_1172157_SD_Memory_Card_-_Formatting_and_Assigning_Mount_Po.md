---
title: "SD Memory Card - Formatting and Assigning Mount Point"
date: 2009-05-28
forum: Hardware
---

### Post by KJU on 2009-05-28
Computer: Acer Aspire One 110A with 8GB Solid State Disk
SD Card: 4GB SD HC Class 6
OS: Ubuntu 9.04 Desktop installed from USB Stick

What I intended was to install Ubuntu (/) in an ext2 primary partition and include a swap extended partition on the SSD, and mount the SD Card as /home. In the Aspire One's left-hand SD slot, it would mount automatically and I'd just leave it there.

The Live Install accepted my manual partitioning setup and formatted everything. For several boots, /home was happy on the SD Card. All seemed okay.

When I inserted an SD Card (FAT format) in the right-hand slot and booted, there were many lines of drama from program 'fsck' including 'dying with exit status 4' and since then the file system on the  LEFT-hand /home card is corrupted.

I don't badly need to know why, so mainly...

Questions:
How can I recreate a FAT32 (or other) file system on the corrupted card? The 'fdisk' command in terminal, and 'GParted' in GUI haven't succeeded, at my hand. My Windows computer won't show either SD Card as a drive, but still presents the 'Safely Remove..' icon. 

Is it possible to use an SD Card safely as I wanted to do - as /home or some other folder (mount point)? Or is it really a bad idea to try?

Thanks,
KJU

---

### Post by ugm6hr on 2009-06-08
I have had similar problems trying to use an SD card; I have now corrupted the card 3 times using ext2, naming it sdhome (ensuring mountpoint of /media/sdhome), and trying to symlink from my user directory to the SD card.

It has not worked well with 9.04; not sure why.

---

### Post by rudeboyintrouble on 2009-06-22
Hi everyone,

I'm trying to revive a 16GB Sony MMS I was using in my PSP.

The card used to work ok as far as I could tell. When it went bonkers, it had been suffering from lots of lost or linked clusters (chkdsk), 
I figured it was because I was taking out the psp improperly or too soon. A couple of times I did pull it out of Ubuntu machine without unmounting it.

In one of these ultimate boot cd's there ought to be an 'unstoppable' formatter. I will check out what I've got and report back. then again, I haven't googled thoroughly enough yet.

I've tried windows format, no success. Ubuntu, gparted, i've tried;

mount -t vfat /dev/sdb1 /media/psp16gb

gparted /dev/sdb1
gparted /dev/sdb

*Could not stat device /dev/sdb - No such file or directory.*

fsck.vfat /dev/sdb1
fsck.vfat /dev/sdb

*open /dev/sdb1:No such file or directory*

Is there a way to low level format an unmountable volume?

Is there a path to a **state** in ubuntu that exists between usb device load and (attempted) FAT load? (for example, ".locked" or /etc/mtab, a dynamicly update file)

or is there a usb viewer anyone would recommend in ubuntu -or- windows? 

Good luck!

---

### Post by ugm6hr on 2009-06-23
> **rudeboyintrouble said:**
> Is there a way to low level format an unmountable volume?

Just write zeros to it.  Or use DBAN or similar program to securely wipe it.

You should then be able to start from scratch, assuming there is no hardware error (which there may be).

---

