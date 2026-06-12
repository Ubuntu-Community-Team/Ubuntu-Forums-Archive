---
title: "Benq 1640 DVD writer fails to read under ubuntu"
date: 2005-08-30
forum: Hardware &amp; Laptops
---

### Post by justThisGuy on 2005-08-30
I have a new BenQ 1640 that works under Windows 2000 (reading and writing disks works fine), but seems to have a probles reading disks under linux using a 2.6 kernel. Is anyone sucessfully running this drive under ubuntu?

I'm running it on an Intel D845PEBT2 motherboard and while you can boot an old version of Knoppix (kernel 2.4) it won't boot later knoppix's or a Suse 9.3 or the Ubuntu 5.04 installer. When reading from the drive under Ubuntu 5.04, I get the following errors when I try and read longer files:

hdc: cdrom_read_intr: Bad transfer size 65534
  This drive is not supported by this version of the driver
end_request: I/O error, dev hdc, sector 28360
Buffer I/O error on device hdc, logical block 7090
hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
hdc: status error: error=0x00
hdc: drive not ready for command
hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
hdc: status error: error=0x00
hdc: drive not ready for command
hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
hdc: status error: error=0x00
hdc: drive not ready for command
hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
hdc: status error: error=0x00
hdc: drive not ready for command
hdc: ATAPI reset complete

Any ideas are welcome.

---

### Post by David Vallner on 2006-02-20
Cunningly hidden in the forums, someone posted that this drive needs DMA activated, which it isn't by default.

It worked for me, so I'll repost it here since the thread title makes it likely for others with this problem to find.

Whack the following into a shell:

  sudo hdparm -d1 -k1 /dev/dvd

(Optionally replace /dev/dvd with the path to your DVD drive if for some strange reason you don't have that symlink.)

---

### Post by TylerH on 2006-03-14
interesting...
i enabled dma using automatix, so maybe it's safe to switch back to my benq drive now

thanks

---

### Post by justThisGuy on 2006-03-29
[QUOTE=David Vallner]Cunningly hidden in the forums, someone posted that this drive needs DMA activated, which it isn't by default.

It worked for me, so I'll repost it here since the thread title makes it likely for others with this problem to find.

Whack the following into a shell:

  sudo hdparm -d1 -k1 /dev/dvd

(Optionally replace /dev/dvd with the path to your DVD drive if for some strange reason you don't have that symlink.)[/QUOTE]


Yeeha! That did the trick for me, too. Thanks!

---

