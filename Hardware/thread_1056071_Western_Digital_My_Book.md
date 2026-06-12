---
title: "Western Digital My Book"
date: 2009-01-31
forum: Hardware
---

### Post by rabat on 2009-01-31
When I plug my Western Digital 500gb USB HDD into a USB port I get the message: 

Cannot Mount Volume The volume 'WD MY BOOK' uses the fat32 file system which is not supported by your system.

The thing I find most odd is that it works fine from a live Ubuntu CD or windows.  I have made sure that it was stopped properly in windows.

Sometimes this message pops-up too: 

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

This is how it shows up on fdisk:

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60801   488384001    b  W95 FAT32


When I try to mount it manually it   sudo mount -t vfat /dev/sdg /mnt/Book/   I get:

 wrong fs type, bad option, bad superblock on /dev/sdg,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is the output from dmesg, but interpreting this is a beyond my limited knowledge.

[  151.624198] ppdev0: unregistered pardevice
[ 1350.990749] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 1350.993652] FAT: invalid media value (0xb9)
[ 1350.993661] VFS: Can't find a valid FAT filesystem on dev sdg.
[ 1467.687554] FAT: invalid media value (0xb9)
[ 1467.687564] VFS: Can't find a valid FAT filesystem on dev sdg.
[ 1481.440213] FAT: invalid media value (0xb9)
[ 1481.440224] VFS: Can't find a valid FAT filesystem on dev sdg.
[ 1531.918638] FAT: invalid media value (0xb9)
[ 1531.918648] VFS: Can't find a valid FAT filesystem on dev sdg.

Thanks to anyone who viewed this long message. I appreciate all of the help on these forums and I love this o/s.

---

### Post by rabat on 2009-01-31
I should also mention that my other 2 small 1gb usb devices work just fine.  I had to format the drive in question as ntfs once, and then back to fat32 using swiss army knife.  I need fat32 unfortunately because I use this drive to watch videos on my xbox 360 and that is the only system it understands.

---

### Post by rabat on 2009-02-03
Well, I searched hi and low on the forums and never did find an answer.  I managed to come up with a solution.  I tried formating the whole drive fat32.  But no matter what I did it would mount read-only.

I finally solved the issue by formatting the drive with gparted to its full capacity -1 mb.  I can't explain it, but it worked great.  I am now back in business and xbox compatible. I have no idea why I had to use less than all the space available.  I figured this out by first making two 250 gb partitions.  

You can get gparted by typing in terminal: sudo apt-get install gparted.

Then run gparted by typing: sudo gparted

It is an awesome tool to have anyway.

---

