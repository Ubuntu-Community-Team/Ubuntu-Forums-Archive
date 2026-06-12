---
title: "fixing a broken hard disk partition table"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by Eupham on 2007-07-30
Somehow I managed to mess up an external hard drive I have pretty good.  It had messed up and I tried to fix it and that didn't work.  I left it for a while and came back to try and fix it a couple of weeks later.  I got a file system on it but that was working weird so I wanted to zero out the disk and start over.  I ran a dd if=/dev/zero and such on the hard drive but now I can't put a file system on it because it looks like a drive that is zero bytes.  It is actually a 200 gb external drive.  Any way to fix this?

---

### Post by hysteresis on 2007-07-30
maybe the ultimate boot cd?

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by Eupham on 2007-07-30
Thanks I'll try that out.  I'm not sure exactly what is wrong but I'm pretty sure it is not a physical malfunction

---

### Post by Eupham on 2007-07-30
That wasn't exactly what I needed.  I just need a way to make the disk know it has 200 gb space.  Right now it looks like it is 0 bytes so I can not partition it because there is no room left.  I ran this 

dd if=/dev/sda of=/dev/sdb bs=8192

and now I do not know how to get the drive to a working state again

---

### Post by hysteresis on 2007-07-30
What brand of drive is it? some brands allow you to go into the drive firmware and change the capacity of the drive (Seagate, for example). I don't know how the dd command could have made that happen, but I guess anything is possible. Seagate Seatools

[http://www.seagate.com/www/en-us/support/downloads/seatools](http://www.seagate.com/www/en-us/support/downloads/seatools)

will allow you to change the capacity of some of their drives.  If you have a different brand, you may have to go to their website to find the right software. Good luck.

---

### Post by Eupham on 2007-07-30
will those tools detect a hard drive connected through usb?  I bought an external case and put a drive in it myself

---

### Post by hysteresis on 2007-07-30
I don't know.  You may have to take the drive out and open a desktop machine to plug it in. Sorry.

By the way, does fdisk  or cfdisk see the drive?

---

### Post by Eupham on 2007-07-30
Yeah that would make things easier but I do not have access to a SATA enabled computer lol

---

### Post by hysteresis on 2007-07-30
if you run sudo cfdisk in a terminal, will it see your drive?

---

### Post by Eupham on 2007-07-30
no, it only shows the internal drive of my laptop and not the external.  As far as I can tell there is no filesystem on the external and no partitions.  It is listed in /dev though as sdb but I do not get 1,2,etc because of no partitions.

if I run

mkfs.ext3 /dev/sdb 

I get

mke2fs 1.40-WIP (14-Nov-2006)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
mkfs.ext3: Device size reported to be zero.  Invalid partition specified, or
        partition table wasn't reread after running fdisk, due to
        a modified partition being busy and in use.  You may need to reboot
        to re-read your partition table.

---

### Post by hysteresis on 2007-07-30
I'm stumped. You may be able to call or email the manufacturers  tech support and they may be able to help you over the phone or even send you some (probably windows) software to fix it. 
Have you tried seagate disk wizard on the ultimate boot cd? I've fixed and formatted even non seagate drives with that program.

---

