---
title: "Ubuntu live CD not listing drives."
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by acidblue on 2005-06-16
I want to try ubuntu before I install to my HD.
So I booted the live CD--which went fine.
However ubuntu dosen't list some of my drives.
I have XP pro on the first drive, a cdrw, dvd, usb HD.
Ubuntu only see's the usb drive and the first cd drive, which is my cdrw,
but lists as cdrom.

Does ubuntu come with NTFS support?
I have a 2 HD system, XP on the first and a fat32 partiton on the second,
both are ATA/IDE not SCSI.

Ubuntu can't see either of them, nor dose it see my DVD drive, which is the 
slave to the cdrw.

On boot up it does detect all my drives and devices
it just doesn't list them under 'Computer' folder.
Does this mean I have to add them manually?

I suppose  I could try: mount /dev/hde
or mount /dev/media/cdrom1, or whatever.
Then add them to my fstab.

Just curious as to why it wouldn't list my other drives,
especially when one of them is just a slave HD with a fat partition.

---

### Post by jerrykenny on 2005-06-17
Maybe the live cd just lacks some of the functionality of the real thing ?

I've never had any problem using IDE cdroms cdrw's with any Linux distro.

I think NTFS support is read-only. so you'll need a FAT partition (maybe 600mb) for shared files between OS's

If you're not sure about it you can back out of the installation before you commit your partitioning changes to the hard-drive (presumably the 2nd FAT one)   In fact if the installer doesnt even see this hard drive you can retreat earlier than that with no harm done.

---

