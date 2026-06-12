---
title: "Need help with DVD-RW drive."
date: 2005-10-31
forum: Hardware &amp; Laptops
---

### Post by S29K on 2005-10-31
I needed a means to backup my MP3 collection so I picked up a Sony DRU-810A DVD-RW and swapped it with my existing DVD-ROM drive.  The device is properly recognized in Device Manager and mounts as hdd.  It will read commercially created data discs, recognize the Ubuntu install disc that I burned from iso, recognize blank DVD-R media and mount an audio disc on the desktop.

Here's the problem.  It won't read the audio tracks in Nautilus or Sound Juicer or Grip or anything!  I've tried several different discs (all of which are recognized fine in my CD-RW drive) but none of them work.  I'm posting this from work so I  don't have the actual listing but my fstab entry for the drive was originally the same as the CD-RW....didn't work.  I tried mirroring the entry for the floppy drive...didnt work.  I have left it like the CD-RW but tried adding 'rw' in front like

/dev/hdd        /media/cdrom1    udf,iso9660 rw,user,noauto  0       0

but it still won't read audio data from a standard CD.

Any ideas?

---

### Post by jvictor on 2005-10-31
I have the same drive,Was a big time pain..  I'd to remove the jumper and turn on dma for the drive.. for things to work smooth . Try what i did , maybe it may help..

---

### Post by S29K on 2005-11-04
I have set DMA on for the drive and even fiddled with the mount points to no avail.  The jumper needs to be set to something as I have two hard drives and two optical drives in my system.

hda - Primary HD
hdb - CD-RW
hdc - Secondary HD
hdd - DVD-RW

I have it set up this way to keep the secondary HD on a different channel than the CDRW as I am currently ripping my fairly large CD collection to MP3 and it supposed to be faster set up this way.

Ultimately it doesn't matter if I get the drive to read audio or not since my other one works fine...it's just one of those things that SHOULD work so I'd like to fixx the problem.

---

