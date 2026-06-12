---
title: "Looking for compatible external hard drive"
date: 2014-08-07
forum: Hardware
---

### Post by lynyl on 2014-08-07
Can somebody recommend an external hard drive of about 500 GB that is compatible with Ubuntu 14.01? Preference is for something that will plug and be recognized out of the box.  I read that you need support for NFS, iSCSI or AoE - not Samba, CIFS, NTFS/FAT 32  -  but who makes them? 
I have a Toshiba Canvio NTFS formatted which is not recognized even by "Disks" in the Dash. Just want to be wiser when buying this time - and not having an early Christmas present lying around!
Thanks for any advice you might have.

---

### Post by TheFu on 2014-08-07
Any HDD can be reformatted for Linux/UNIX file systems. The USB chip interface for the drive may NOT be supported by Linux, however.

External drives come in many different sorts - that device you have now is USB and limited.

If you are looking for Network Attached Storage - THAT is a very different question. You'll have to check the specifications for every NAS machine that you look at to ensure it supports the protocols that are important to you.  The versions that support iSCSI are usually not in the home-market price range, so most of us just build it ourselves with either Ubuntu or FreeNAS (or folked versions).

I can't speak at all about anything in the Ubuntu GUI for managing disk - never use it. If you stay with gparted and parted, you should be safe for all sorts of Linux file systems - provided it isn't a block network version or LVM.

[http://www.smallnetbuilder.com/](http://www.smallnetbuilder.com/) is a place to start - be aware that he seems to have gone Windows only (CIFS) in my recent reading - I haven't been in the market for a NAS storage device in a few years.  Also - I don't think you will find any NAS with AoE support.

It might be important to group the different things you've listed cause some are file systems, others are network file system protocols and the others are network block device protocols. These are VERY different.
* AoE / iSCSI / Fibre Channel / eSATA / etc.
* NFS / CIFS / Samba / DFS / AFS / and perhaps DLNA could be in this group
* EXT4/3/2 / BTRFS / NTFS / vFAT / XFS / JFS / and probably 20 others.

Hope that helps.

---

### Post by lynyl on 2014-08-07
I guess my throwing out all those file names muddied the waters - sorry!
I don't want network attached storage and I don't want to build anything. I just want a "little" (500gb is fine) external HD to store all my photos as a backup. I want it to be usb and able to be recognized by Ubuntu 14.01 on plug-in, like my old Seagate which is as big as a book, years old and that I want to replace. Brands would be helpful or what file format I need to look for that works - anything so I can be smarter than the clerk who says,"Oh, this will work!".

---

### Post by Mark Phelps on 2014-08-07
WD, Seagate, Toshiba, and others make 2.5" portable external drives 500GB (and larger) that are powered entirely through a USB cable.  They will most likely be formatted FAT32, but you can easily plug them in and reformat them to whatever you want.  Just avoid anything that claims to come with software preloaded (like some WD passport drives), as that nearly always works only in Windows.

---

### Post by Yellow Pasque on 2014-08-07
> Just avoid anything that claims to come with software preloaded

No need to avoid it. It will be gone once you format the drive...

I have a Toshiba Canvio 1 TB that works well with Linux (I shrunk the pre-formatted NTFS volume in half and use the other half as ext4).

---

### Post by TheFu on 2014-08-07
> **lynyl said:**
> I guess my throwing out all those file names muddied the waters - sorry!
I don't want network attached storage and I don't want to build anything. I just want a "little" (500gb is fine) external HD to store all my photos as a backup. I want it to be usb and able to be recognized by Ubuntu 14.01 on plug-in, like my old Seagate which is as big as a book, years old and that I want to replace. Brands would be helpful or what file format I need to look for that works - anything so I can be smarter than the clerk who says,"Oh, this will work!".

I've never heard of any HDD not working with Linux - except if it was broken.  I have seen strange incompatibilities between USB ports and USB devices - but those are few and rare to the point that I've never worried about it unless USB3 is involved.

Is there a 14.01?  Non-experts should probably stay with 14.04 until 16.04 is released in a few years and should probably avoid the intermediate releases unless there is a really important need, since those only get 6-9 months of patches/support.

---

### Post by TheFu on 2014-08-07
> **lynyl said:**
> I guess my throwing out all those file names muddied the waters - sorry!
I don't want network attached storage and I don't want to build anything. I just want a "little" (500gb is fine) external HD to store all my photos as a backup. I want it to be usb and able to be recognized by Ubuntu 14.01 on plug-in, like my old Seagate which is as big as a book, years old and that I want to replace. Brands would be helpful or what file format I need to look for that works - anything so I can be smarter than the clerk who says,"Oh, this will work!".

I've never heard of any HDD not working with Linux - except if it was broken.  I have seen strange incompatibilities between USB ports and USB devices - but those are few and rare to the point that I've never worried about it unless USB3 is involved.

Is there a 14.01?  Non-experts should probably stay with 14.04 until 16.04 is released in a few years and should probably avoid the intermediate releases unless there is a really important need, since those only get 6-9 months of patches/support.

---

### Post by lynyl on 2014-08-07
Well, this time I plugged it in to a different usb port and the computer recognized it! And I can transfer files to it, so I'm good! Thanks!

---

### Post by Vladlenin5000 on 2014-08-08
> **lynyl said:**
> Well, this time I plugged it in to a different usb port and the computer recognized it! And I can transfer files to it, so I'm good! Thanks!

Yeah, the usual... Please mark this thread as solved. Thank you.

---

