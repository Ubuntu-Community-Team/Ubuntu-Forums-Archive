---
title: "External HDD is crap on multiple OS's"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by Griff on 2006-11-13
My WD external USB hdd is now no longer being recognized by Windows or Ubuntu.  It's receiving power, but it is not being listed under ```
sudo fdisk -l
```
Any ideas what the malfunction could be?  There are some things on it I desperately need.  Like old pictures and whatnot.  I used it for all media backups.

Thanks,
Griff

---

### Post by taurus on 2006-11-13
If none of the OS can see it, then perhaps it's just a file of junk!  See if the BIOS detect it or not and if the BIOS doesn't detect it, sorry but it's a goner...  Maybe some computer stores can recover stuff on it for you with a fee, of course!

---

### Post by jamesrose on 2006-11-13
Do you happen to be using a USB hub? I was using a usb hub, wondering why my external HD wouldnt work, soon as i plugged it into a direct port it worked fine :)

---

### Post by Griff on 2006-11-13
> **jamesrose said:**
> Do you happen to be using a USB hub? I was using a usb hub, wondering why my external HD wouldnt work, soon as i plugged it into a direct port it worked fine :)
It's sort of on a hub.  I'll try putting in in an actual USB port on the MOBO though to see if that does anything next boot.  However, it worked fine before so I don't have much hope. :(

---

### Post by Griff on 2006-11-13
I looked in the BIOS and didn't see anything and also put the drive into another port, but in windows I see this now (pic below).  I'm not sure what to make of it.  Any ideas what to do?  My fiance has some pics of some past animals on there that I'd really like to recover for her.

Thanks,
Griff

---

### Post by l:x on 2006-11-14
What is "lsusb" telling you when you connect it when in Linux?

---

### Post by Griff on 2006-11-15
> **l:x said:**
> What is "lsusb" telling you when you connect it when in Linux?
```
stephen@ubuntuPC:~$ lsusb
Bus 003 Device 007: ID 054c:014f Sony Corp.
Bus 003 Device 006: ID 03f0:5611 Hewlett-Packard
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
stephen@ubuntuPC:~$
```
The first device is a external dvd writer and the HP is a printer.

---

### Post by Griff on 2006-11-17
So I solved the problem today!  Here's the solution...

Bad USB cable!

I've never had a USB cable just stop working, but that's exactly what this one did.  I exchanged it for another one and now no more problems.  I am overjoyed! Woo!:mrgreen: 

Thanks everyone!
Griff

---

### Post by Exakun on 2006-11-27
I am having a similar problem with my 300GB Maxtor SATA external hard drive, which is connected through a Thermaltake SATA/IDE to USB encasement. It has been working absolutely perfectly until an hour or so ago. I am able to detect it (with some difficulty) in Windows, but it does not recognize at all in Ubuntu. It typically appears as "media/usbdisk" (assuming I have nothing else plugged in) but that location is not in the filesystem.

I followed the steps posted earlier in the thread, including trying different ports, restarting the power to the disk (which results in the disk use light to constantly be on) and swapping out the USB cable. Ubuntu still cannot see the drive.

I tried running a chkdsk in windows and it found something (Typical of Windows not telling you what the problem *actually is*), but it claims not to have enough hard drive space to recover it. Seeing as I don't have any 100GB files, I have no idea what the problem is.

Here are the results from running the commands from previous posts:
```
exaxxion4096@exanotebook:~$ sudo fdisk -l

Disk /dev/sda: 59.8 GB, 59814236160 bytes
255 heads, 63 sectors/track, 7272 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         523     4200966   83  Linux
/dev/sda2             524         655     1060290   82  Linux swap / Solaris
/dev/sda3             656        2177    12225465   83  Linux
/dev/sda4   *        2178        7272    40925587+   7  HPFS/NTFS
```
```
exaxxion4096@exanotebook:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c518 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
```
The logitech device is a USB wireless mouse receiver.

Thanks in advance for any help on this issue.

---

