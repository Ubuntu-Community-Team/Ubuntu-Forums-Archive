---
title: "Can't unmount NTFS SATA partitions"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by tseliot on 2005-07-24
Hi, this problem is really annoying. I have 2 harddisks: 1) Maxtor PATA 120gb (with Ubuntu Hoary 64) 2)Seagate SATA 160gb (with Windows XP).

The problem is that I can mount and read (I've got lots of data on it) my SATA drive but when I try to unmount its partitions the computer hangs. I tried with the command "umount -l" and I got to unmount just one partition, the system froze while attempting to unmount the others partitions. If I try to shut down the system without unmounting my SATA partitions it closes KDE successfully but in the command line it hangs (though the cursor doesn't stop blinking, however I can't reboot with ctrl+alt+del) the  when it says "unmounting local filesystems".

I've got kernel 2.6.12.3-3 from Ubuntu Breezy (but I've got Hoary) could this be the problem? However I want to compile a new Kernel (from a vanilla one). Is there something I should set in the kernel in order to solve the problem. I've read somewher on the web that my mobo (MSI RS480M2-IL) uses "sata_sil" for its controller .

This is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/sda2       /media/windows2 ntfs noauto,users,exec,ro,umask=000 0 0
/dev/sda5       /media/windows5 ntfs noauto,users,exec,ro,umask=000 0 0
/dev/sda6       /media/windows6 ntfs noauto,users,exec,ro,umask=000 0 0
/home /chroot/home none bind 0 0
/tmp /chroot/tmp none bind 0 0
/dev /chroot/dev none bind 0 0
/proc /chroot/proc proc defaults 0 0
/media/cdrom0 /chroot/media/cdrom0 none bind 0 0
/media/cdrom1 /chroot/media/cdrom1 none bind 0 0
/usr/share/fonts /chroot/usr/share/fonts none bind 0 0

As you can see I'm using a chroot 32bit but the problem existed before I set it up.

Any suggestions?

Thanks in advance

Update: It has been solved in  kernel 2.6.12.4 (from Breezy)

---

