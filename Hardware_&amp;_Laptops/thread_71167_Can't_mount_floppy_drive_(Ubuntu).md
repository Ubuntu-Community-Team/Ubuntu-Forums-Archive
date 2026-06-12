---
title: "Can't mount floppy drive (Ubuntu)"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by dn889312 on 2005-10-02
*mount: I could not determine the filesystem type, and none was specified*

I don't know what that means, or what mounting even is, so can someone tell me what to do?

---

### Post by Ruddigger on 2005-10-02
sometimes the module for mounting fat filesystems isn't loaded by default, check with lsmod
so you have to load them manually with modprobe, and I would add them to /etc/modules so you don't have to do that again.

---

### Post by dn889312 on 2005-10-02
I'm kind of a newb, so so can you please explain to me exactly how to do these things?

---

### Post by dn889312 on 2005-10-02
Well, by formating one of the disks it stopped the mount error, but I can't fit a 1.4 boot disk image onto the disks. Any one know why?

---

### Post by David Haas on 2005-10-02
dn889312--Because I don't know how where you are now with mounting the floppy, I'll go through all the steps. First, format the floppy with the terminal (shell) command "fdformat /dev/fd0" (without the quotes). Then add the Linux filesystem to it with the command "mke2fs /dev/fd0" (mke2fs is the filesystem, fd0 is the floppy file in the directory /dev). Then you ready to mount the floppy. One mounts the floppy (which Linux treats as a file) in a directory--any empty directory, in fact. But it's most convenient to mount it in a directory listed in /etc/fstab. So, I'd change to the directory /etc in your terminal and at this directory enter the command "gedit fstab" to open the fstab file in the editor (gedit). Then you can change (edit) the /dev/fd0 line to "/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0". The /media/floppy0 is the directory where you will mount the floppy (this is just a convenience). Make sure that you have the floppy0 directory in the /media directory--it should be there by default in Ubuntu. After editing fstab as above, you can then mount the floppy with the command (as root--"sudo -s") "mount /media/floppy0" (again, without the quotes). When finished storing stuff on the floppy, unmount as root with the command "umount /media floppy0' (it is "umount", not "unmount"). Of course, once you've edited fstab and have the floppy formatted, with the filesystem on it, mounting is quick with "mount /media/floppy0".

I hope this helps.

David

---

