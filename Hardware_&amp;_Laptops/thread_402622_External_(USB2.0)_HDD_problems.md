---
title: "External (USB2.0) HDD problems"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by eggybaby on 2007-04-06
Please help; My external HDD isn't recognized. It works on my Fedora box but not Ubuntu.
I'm a noob. I searched desperately before posting for help.

I ran $dmesg immediatly after plugging device in and saw no reference to USB at the end.
******************
.
.
[  207.572749] Bluetooth: RFCOMM socket layer initialized
[  207.572802] Bluetooth: RFCOMM TTY layer initialized
[  207.572813] Bluetooth: RFCOMM ver 1.7
balthazar@Balthazar:/sys/block$ 
********************************

I ran:
$lsusb  ( shows nothing)

I ran:
$sudo sh -c "echo 120 > /sys/block/sda/queue/max_sectors_kb"
...but the /queue directory doesn't exist

The 'Device Manager' *does* show a USB device detected: (82371AB/EB/MB PIIX4 USB)

I've tried several other devices too; PSP, thumb drive, mp3 player - all to no avail.

Can anyone tell me what to try next? Thanks alot.

---

### Post by SendDerek on 2007-04-06
What's the filesystem?

If it's NTFS, then you may need a windows machine in order to perform a disk check on that Ext.HDD.

It happens to me occasionally when I forget to properly eject the drive and I end up unplugging it and it messes the disk up.  I have to boot into windows to perform the Disk Check and then eject that correctly (Safely Remove Hardware), and then it's good to go again.

> 
I've tried several other devices too; PSP, thumb drive, mp3 player - all to no avail.


Oops... I failed to see that.  I have no idea then.  Thumb Drives are usually FAT32 and usually work just fine.  MP3 players could be a little difficult, and I'm not even going to try to explain a PSP.

---

### Post by eggybaby on 2007-04-06
thanks anyway;
I didn't mention; I even formated the HDD to 'ext3' (beforehand from a WinXP machine using 'Partition Magic') since I knew I'd be using it only in linux.
Also, I have a 2nd external HDD that is FAT (or FAT32). It works to both my XP 'and' Fedora but not to Ubuntu.

---

### Post by eggybaby on 2007-04-06
I'm a dumb a** 
The BIOS's USB support was 'disabled'. Put it to 'enabled', booted, and it found the HDD.

---

### Post by SendDerek on 2007-04-08
> **eggybaby said:**
> I'm a dumb a** 
The BIOS's USB support was 'disabled'. Put it to 'enabled', booted, and it found the HDD.

Haha!  :) 

Oh man... I hate when that kind of stuff happens!

---

