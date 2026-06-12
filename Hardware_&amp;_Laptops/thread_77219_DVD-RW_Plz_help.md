---
title: "DVD-RW Plz help"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by jvictor on 2005-10-16
Hi guys!

Having big time probs with my dvd-rw ONLY on LINUX !! On windows it works like a breeze.

No matter whever i download from,whichever torrent i use or whichever arch (x86 / 64)  of ubuntu 5.04 - 5.10 i use, the install fails either at 13 % while copying e2fsprogsXXX.udeb or 23% jfsutilsXXX.udeb

Ironically there wasnt any problem if i used the ship it cds of warty !

So i had to connect my old cd-r drive to get ubuntu installed.

Pain starts...

Cant burn on to a CD-RW

gnomebaker segfaults

nautilus writes binary content like jpg images as text/plain files !

System hangs if i try to erase a cdrw, and need to hard-reboot to get out

Cant eject the media once this happens

juby@powercube:~$ eject
eject: unable to eject, last error: Invalid argument


Some gen info which may be of help...
-------------------------------------

When i put a CD-R

juby@powercube:~$ sudo hdparm -t /dev/hdc

/dev/hdc:
 Timing buffered disk reads:    4 MB in  4.00 seconds = 1022.88 kB/sec

When i put CD-RW

/dev/hdc:
 Timing buffered disk reads:  read(2097152) returned 1966080 bytes
juby@powercube:~$ sudo hdparm -t /dev/hdc

/dev/hdc:
 Timing buffered disk reads:  read() failed: Input/output error

juby@powercube:~$ eject
eject: unable to eject, last error: Invalid argument


The tail -f o/p of the /var/log/messages shows this 

t 16 22:15:25 localhost kernel: [  134.755363] hdc: ATAPI reset complete
Oct 16 22:15:25 localhost kernel: [  134.755375] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }

hdparm once the dvd rw drive hangs is given below

juby@powercube:~$ hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

My machine config

AMD 64 3000+ running 5.10 x86_64
1 G ram
via graphics (onboard) vesa driver
rtl8139 lan card (onboard)
ac97 audio (onboard)
SONY DRU810-A DVD RW( the mother of all pains !)

---

### Post by earobinson on 2005-10-16
k3b is a great program for burning isos
for me the only way i can burn dvds seems to be nautclis-burner :(

i just got my dvd burner yesterday

---

### Post by jvictor on 2005-10-16
At least we must be able to erase a disc !

Nautilus says it only needs 1193046 hours, 28 mins and 36 secs to write a 230 kb jpg image @ 4x speed !!!

Started wondering whether its a kernel level issue coz the machine itself hangs !

---

### Post by jvictor on 2005-10-17
Have reverted to hoary .. far far stable than breezy . DV writer problems have disappeared.

---

