---
title: "SATA2 HD Ticks/Squeaks?"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by ~LoKe on 2006-10-30
I'm trying to get this new Seagate SATA2 drive up and running, but once plugged in and connected, it either ticks or squeaks when I'm trying to boot up.  I don't know if this is normal or not.  My BIOS is **not** detecting the SATA2 drive.

Is there any way I can find out if it's a problem with the drive, my motherboard/BIOS or otherwise?  I don't have another computer to test the drive in.

I see no /sda in /dev, either.

---

### Post by dogon on 2006-10-30
Ticks and squeaks don't sound good to me.

As a root user ("sudo -i" from terminal)
you can try to list what disks are available ("fdisk -l" (thats an L not an I)

If that does not show the drive then linux does not know about it.

Possibly your bios needs an upgrade. Because bios should always detect your disk. 

If I were you I'd claim the disk faulty because of the ticks and squeeks and exchange it for another. Since its brand new you should still have warranty. If that does not solve the problem then you can always try upgrading the bios. 

You could go the other way round and upgrade bios first but you'll always have the uneasy feeling about the disk.

---

### Post by ~LoKe on 2006-10-30
It makes the sound only when I'm trying to boot, because I think it's trying to detect the disk but it can't.  fdisk -l is showing nothing about my SATA drive, only my two IDE's.

I'll just RMA the thing.  Thanks for the help!

---

