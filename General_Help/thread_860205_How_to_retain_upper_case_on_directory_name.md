---
title: "How to retain upper case on directory name"
date: 2008-07-15
forum: General Help
---

### Post by satimis on 2008-07-15
Hi folks,


How to retain upper case on directory name copied on mounted pendrive.


e.g
1)
$ sudo cp -r AAA-dir /mnt/pendrive

$ ls /mnt/pendrive```

aaa-dir

```
All changed to lower case


2)
Strangely

$ sudo cp -r Abc-dir /mnt/pendrive

$ ls /mnt/pendrive```

Abc-dir

```
Upper/lower case can be retained.


Please advise.  TIA


B.R.
satimis

---

### Post by fsmithred on 2008-07-17
One solution would be to reformat the pendrive to a filesystem that's case-sensitive. I don't know if there are other solutions. 

I just tested it, and I get slightly different results. I created TEMP/testfile1 and Temp/testfile2. Then I did a 'cp -r' on TEMP and then on Temp.

In Hardy, it copied TEMP and its contents to the pendrive without changing case, and then it added testfile2 to TEMP on the pendrive.

In debian etch, it copied TEMP and its contents without changing case, then it refused to create Temp, because it already existed (even though it was showing up as TEMP.)

---

### Post by satimis on 2008-07-17
> **fsmithred said:**
> One solution would be to reformat the pendrive to a filesystem that's case-sensitive. I don't know if there are other solutions. 

I just tested it, and I get slightly different results. I created TEMP/testfile1 and Temp/testfile2. Then I did a 'cp -r' on TEMP and then on Temp.

In Hardy, it copied TEMP and its contents to the pendrive without changing case, and then it added testfile2 to TEMP on the pendrive.

In debian etch, it copied TEMP and its contents without changing case, then it refused to create Temp, because it already existed (even though it was showing up as TEMP.)
Hi fsmithred,


Thanks for your advice.


I'm using the pendrive transferring data between Linux and Windows boxes.  FAT16 is not case-sensitive.  Any suggestion?  TIA


satimis

---

### Post by fsmithred on 2008-07-17
I think you could use ntfs, but I've never tried it.

This might help -
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by MobiusNZ on 2008-07-17
> **satimis said:**
> Hi fsmithred,


Thanks for your advice.


I'm using the pendrive transferring data between Linux and Windows boxes.  FAT16 is not case-sensitive.  Any suggestion?  TIA


satimis

Use FAT32. Most usb sticks are formatted this way these days. FAT32 isn't fully case sensitive either, but it will remember the case you have set.

(ie you can create aAa, but it will clash with aAA)

---

### Post by satimis on 2008-07-17
> **MobiusNZ said:**
> Use FAT32. Most usb sticks are formatted this way these days. FAT32 isn't fully case sensitive either, but it will remember the case you have set.

(ie you can create aAa, but it will clash with aAA)
Noted and thanks


satimis

---

### Post by dcstar on 2008-07-18
> **fsmithred said:**
> I think you could use ntfs, but I've never tried it.


NTFS (or any filesystem) works fine on USB stick drives - the only issue with any Journaling filesystem (like NTFS) are the extra writes that come with them.

People have to keep in mind that USB solid state devices still have a finite number of times that you can trigger internal write cycles (although these days it is quite large), so moving from FAT to NTFS will cause the eventual failure time to be reduced.

I have changed USB drives to NTFS so they can take >4GB files because I now use them as an economical way to back up a server database nightly - replacing DDS tapes.

It's a lot cheaper these days to use a pile of USB drives than purchase and install SCSI DDS tape backup infrastructure - and the USB drives can be left on a magnet without erasing their data......   :-)

---

### Post by satimis on 2008-07-18
> **fsmithred said:**
> I think you could use ntfs, but I've never tried it.

This might help -
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
Hi fsmithred,


Thanks for your link.  It is interesting.  I'll find time testing it.  I never ran ntfs on Linux before except on Windows, more than 10 years ago.


If only working on Linux and Unix OS which filesystem will be case sensitive?  TIA


B.R.
satimis

---

### Post by satimis on 2008-07-18
> **dcstar said:**
> NTFS (or any filesystem) works fine on USB stick drives - the only issue with any Journaling filesystem (like NTFS) are the extra writes that come with them.

People have to keep in mind that USB solid state devices still have a finite number of times that you can trigger internal write cycles (although these days it is quite large), so moving from FAT to NTFS will cause the eventual failure time to be reduced.

I have changed USB drives to NTFS so they can take >4GB files because I now use them as an economical way to back up a server database nightly - replacing DDS tapes.

It's a lot cheaper these days to use a pile of USB drives than purchase and install SCSI DDS tape backup infrastructure - and the USB drives can be left on a magnet without erasing their data......   :-)
Hi dcstar,


Thanks for your advice.


Another thought the filesystem on my Linux boxes are either ext2/ext3 including Unix box/OpenBSD.  I can format the USB pendrive ntsf.  Can I copy/move files from Linux/Unix box on it and vice versa?  TIA


B.R.
satimis

---

### Post by fsmithred on 2008-07-18
I think all the common linux/unix filesystems are case sensitive. I'm sure about ext2/3 and Reiser and whatever Zenwalk uses as their default.

The link I gave you has instructions for what you need to do to be able to write to ntfs in linux, so yes, you can copy files back and forth between linux and windows. I don't know about BSD.

---

