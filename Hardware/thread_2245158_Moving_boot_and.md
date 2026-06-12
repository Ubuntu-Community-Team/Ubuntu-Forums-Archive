---
title: "Moving /boot and /"
date: 2014-09-21
forum: Hardware
---

### Post by SJLPHI on 2014-09-21
Hey, I have a laptop Lenovo T410S.

I currently have an mSATA  16gb ssd from E530 which is not in use in any way.

On my T410S I have installed on the 1.8" HDD with separate 500mb /boot partition, 2GB swap and rest allocated to  "/" including home and etc.

I want to stick my mSata on T410S (It does have compartment)
and use it for
/boot
and
/

and keep the /home in my HDD.

Any advices?

Lately I am finding that my main HDD might be too old and sometimes fails to boot. I am suspecting that it has been damaged. I make backups of most of the things that I need and I wish to have a stable boot and root partition such that I can simply swap out and clone my HDD to an SSD (Once I can afford a decent one)

---

### Post by weatherman2 on 2014-09-21
BACKUP ANY IMPORTANT DATA ON YOUR DRIVE TO SOME OTHER DRIVE OR DEVICE before attempting any of this!  One tiny mistake and you could wind up erasing files forever. (Of course, with a possibly failing hard drive, I would run S.M.A.R.T. tests on it too.)

There is no need for a separate /boot partition unless you are booting multiple Linux distros - or if you already have Windows and your initial partitions are not aligned to a 2048 byte boundary.  If you can't explain why you need /boot you almost certainly don't need one.  I would combine them when you copy to the SSD.

To move / (and combine /boot there) onto the 16GB SSD (which should be adequate for both, on a typical Linux installation), I would do this, in general:

- boot a live USB Linux
- Erase the 16GB partition on the SSD (assuming you have nothing on there of use), create a new ext4 partition there, and format it.
- Assume you leave swap partition on HDD
- Create temporary mount points of old / (which will become /home when you are done), old /boot, and new /.
- copy everything from old / to new / EXCEPT /home (I would use "rsync" in a terminal with the --exclude option)
- Create a /JUNK folder in top level directory of old /, move all folders from old / in there.  (You can erase them later after you are successfully booting from the SSD)
- Move everything in old /home up to top directory of HDD partition
- edit the fstab file of new / to change mount point of / and add mount point for /home on HDD.  Use "sudo blkid" from a commandline to get UUID of new partition and old / now new /home partition if you need it.
- install Grub and update Grub on SSD.  I prefer the "chroot" method for installing/updating Grub.  (Google for "ubuntu grub chroot" and find the instructions there.)
 
#Do ALL OF THIS from a live USB boot of Linux.

If you need specific instructions for any step, just ask.

---

### Post by SJLPHI on 2014-09-21
Unfortunately I found out that my BIOS does not recognize the msata. I will have to go with the whole 1.8" SSD which is a little too expensive in my opinion. I will refer to this thread for future reference. Thank you.

---

