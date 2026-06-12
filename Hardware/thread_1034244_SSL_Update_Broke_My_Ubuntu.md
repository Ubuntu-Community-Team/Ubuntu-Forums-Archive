---
title: "SSL Update Broke My Ubuntu"
date: 2009-01-08
forum: Hardware
---

### Post by jbrice on 2009-01-08
Ubuntu gurus - your help is needed!
After installing the latest updates to 8.04 - consisting of only of SSL patches as far as I could see - my laptop refused to start on re-booting. 
I'm using the standard encrypted file system setup on this laptop and when I tried booting using the recovery option, I could see that the problem was that the encrypted partition was not being found.

After some digging:
- I can boot OK using the previous version of Linux (2.6.24-16)
- the file initrd.img-2.6.24-22-generic seems to have been updated as part of the SSL patch. I tried replacing this file with the .bak version and the laptop boots OK.

I'm guessing that the failure to find the encrypted file system is probably down the new initrd.img file using the wrong uuid - and this is possibly a hangover from having to restore the system from a backup where uuid issues lurked around every corner (see [here]("http://ubuntuforums.org/showthread.php?t=1012103") for the thread detailing that saga).

Where do I go from here? Is it possible to examine/edit the initrd.img file to check out my theory about the UUID error?

TIA

James B.

---

### Post by jbrice on 2009-01-08
Apologies for commenting on my own post...

Having dug deeper, I can report the following:

- the file initrd.img-2.6.24-22-generic appears to have been replaced by an updated version dated yesterday (7-Jan.-09) - what would have caused a new version to be generated? The SSL patch (tho. that was installed this morning)?

- I found out how to extract, edit and re-package the initrd file - the info. is at [http://bbs.archlinux.org/viewtopic.php?pid=282849](http://bbs.archlinux.org/viewtopic.php?pid=282849) and fixed the incorrect uuid (in /conf/conf.d/cryptroot). However there are now problems inserting modules etc. during boot. (Later - warning about inserting padlock.sha seems to be known and harmless bug.)

- Reverting to the .bak version of initrd.img-2.6.24-22-generic and all works fine.

What is going on here??!!

Later - it seems that the UUID for the physical encrypted container partition is held /etc/crypttab and this is used by update-initramfs to regenerate the initrd.img file whenever a kernel-related update takes place. If the UUId in /etc/crypttab is wrong, the boot process in the updated system stalls while looking for a non existent-physical partition.

---

