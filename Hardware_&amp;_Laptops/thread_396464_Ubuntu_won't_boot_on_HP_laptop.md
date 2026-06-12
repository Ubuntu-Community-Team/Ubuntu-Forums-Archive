---
title: "Ubuntu won't boot on HP laptop"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by EricJD on 2007-03-29
Hello,

I'm trying to install 6.06 (only install disc I have on hand) on my HP laptop, a Pavilion zt1000.

When I put the disc in and boot the laptop up, I get this:

> 1200 Mhz Mobile Pentium III /M CPU
Intel Processor Update Rev 01Dh Complete
External Cache: 512K installed
Boot CD-ROM Type: Non-Emulation Booting

ISOLINUX 3.11 Debian-2006-03-16 isolinux: Image checksum error, sorry...

Boot failed: press a key to retry...

Anyone know what's wrong? I'm pretty sure it's not a bad download, because this is an official CD I got from shipit.

---

### Post by azemute on 2007-03-29
> 
ISOLINUX 3.11 Debian-2006-03-16 isolinux: Image checksum error, sorry...

Checksums are quick calculations to see if all the data you expect is there. If it fails, something seems to be amiss. At first I'd say that your disk may be be scratched or was corrupted in some fashion, though it could also be an issue with the disk drive as well. Do other disks work in the drive? [Or, does that disk work in other drives?]

Re-download / Re-burn, you can also check the MD5 if you're so inclined.

---

### Post by EricJD on 2007-03-29
> **azemute said:**
> Checksums are quick calculations to see if all the data you expect is there. If it fails, something seems to be amiss. At first I'd say that your disk may be be scratched or was corrupted in some fashion, though it could also be an issue with the disk drive as well. Do other disks work in the drive? [Or, does that disk work in other drives?]

Re-download / Re-burn, you can also check the MD5 if you're so inclined.

Yes, this disc works fine in other computers..

Okay, I tried another (6.10) install disc and it doesn't work either, it gives me the same error.

---

### Post by azemute on 2007-03-29
To me, that screams a mis-aligned [or otherwise damaged] disk drive.

Have you ever had problems with that specific drive in the past? If not, it may just be some dust or particulate has fallen onto the lens. It could also be one of a number of weird semi-unique errors you can get from BIOS/BoodFromCD setups [I've seen a number of them in the past]

A serious consideration may be seeing if /any/ disks work in the drive [very tough without an OS] or whether any other bootable disks work... namely non-Debian based ones.

---

### Post by drpaul on 2007-03-29
.I have a new hp notebook. Dapper failed to install for me, but Edgy works fine

HTH

Paul
]

---

### Post by Georock on 2007-03-30
i   have  a  hp  3141,i will  try 7.04  later.

---

### Post by greeting on 2008-04-06
I have just cured this problem, with a little help from HP, on my Pavilion zt1162...  Your laptop cannot boot from torito-style CDs without a BIOS update, which is available from the HP website at <<  [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-9854-1&lc=en&cc=us&lang=en&os=181&product=81335&dlc=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-9854-1&lc=en&cc=us&lang=en&os=181&product=81335&dlc=en)  >>

It makes a boot floppy. If you have no USB floppy drive, use another machine that has a floppy. Then Google for utilities to make a CD or USB Stick to emulate a boot floppy (your CD burner might do a boot-floppy-cd for you).

As the laptop starts with the cd or USB in place, tap ESC for the boot menu, choose your device ...and cross your fingers :o)

REMEMBER that doing this wrong, or having it fail, can turn your laptop into an unrecoverable doorstop!!!

---

