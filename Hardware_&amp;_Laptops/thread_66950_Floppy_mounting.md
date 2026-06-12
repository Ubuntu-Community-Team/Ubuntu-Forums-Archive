---
title: "Floppy mounting"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by chrisndebb on 2005-09-18
When I try to mount the floppy drive, I get the error message "mount: I could not determine the filesystem type, and none was specified". Doesn't matter what is on the disk, I get the same message each time.

Any ideas?

---

### Post by sabitha on 2005-09-19
you can use "sudo mount -t vfat /dev/fd0 /media/floppy0" that work for me  :smile: or u can edit /etc/fstab 
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

---

### Post by David Haas on 2005-09-19
chrisendebb--This reply that I wrote in August to another with a floppy-mounting problem may be helpful to you. The error message you received indicates that you hadn't put a filesystem on the floppy.

"Floppies work fine on Ubuntu. Because I don't know how much you've done with the floppy so far, I'll go through all the steps. First, format the floppy with the terminal (shell) command "fdformat /dev/fd0" (without the quotes). Then add the Linux filesystem to it with the command "mke2fs /dev/fd0" (mke2fs is the filesystem, fd0 is the file representing the floppy in the /dev directory). Then you are ready to mount the floppy. Since you know about /etc/fstab, I'd change to the directory /etc in your terminal and at this directory enter the command "gedit fstab" to open the fstab file in the editor (gedit). Then you can change (edit) the /dev/fd0 line to "/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0". The /media/floppy0 is the directory where you will mount the floppy (this is just a convenience). Make sure that you have the floppy0 directory in the /media directory--it should be there by default in Ubuntu. After editing fstab as above, you can then mount the floppy with the command (as root--"sudo -s") "mount /media/floppy0" (again, without the quotes). When finished storing stuff on the floppy, unmount as root with the command "umount /media floppy0' (it is "umount", not "unmount"). Of course, once you've edited fstab and have the floppy formatted and with the filesystem on it, mounting is quick with "mount /media/floppy0".

I hope this helps.

Enjoy Ubuntu!"

David

---

