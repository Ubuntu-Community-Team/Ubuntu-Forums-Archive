---
title: "partitioning disk space problem"
date: 2005-12-12
forum: Installation &amp; Upgrades
---

### Post by Marc Higgins on 2005-12-12
Help please, i didn;t leave enough room on my /usr partition, is there any way i can move it to the / partition post install?

Partition table looks as follows

~~~~~~~~~~~~~~~~~~~~~~~~
From fdisk
~~~~~~~~~~~~~~~~~~~~~~~~
Command (m for help): p

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        5226    41945715    7  HPFS/NTFS
/dev/sda3           19453       19453           0+  83  Linux
/dev/sda4            5227       19452   114270345    5  Extended
/dev/sda5           19268       19452     1485981   82  Linux swap / Solaris
/dev/sda6   *        5227        5955     5855629+  83  Linux
/dev/sda7            5956        6320     2931831   83  Linux
/dev/sda8            6321        6685     2931831   83  Linux
/dev/sda9            6686       10332    29294496   83  Linux
/dev/sda10          10333       19267    71770356   83  Linux

Partition table entries are not in disk order

~~~~~~~~~~~~~~~~~~~~~~~~
from df
~~~~~~~~~~~~~~~~~~~~~~~~
admin@edubuntu:~$ sudo df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda6              6.0G   681M   5.0G  13% /
tmpfs                  260M      0   260M   0% /dev/shm
tmpfs                  260M    13M   247M   5% /lib/modules/2.6.12-9-386/volatile
/dev/sda9               30G   2.1G    27G   8% /home
/dev/sda10              73G    55G    14G  80% /media/backups
/dev/sda2               43G   8.2G    35G  19% /media/windows
/dev/sda7              3.0G   2.7G   153M  95% /usr
/dev/sda8              3.0G   219M   2.6G   8% /var

~~~~~~~~~~~~~~~~~~~~~~~~
my fstab
~~~~~~~~~~~~~~~~~~~~~~~~

admin@edubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda9       /home           ext3    defaults        0       2
/dev/sda10      /media/backups    ext3    defaults        0       2
/dev/sda2       /media/windows  ntfs    defaults        0       0
/dev/sda7       /usr            ext3    defaults        0       2
/dev/sda8       /var            ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

would really appreciate some help on how to move the /usr to the / partition & reclam the space. 

Don't have partmagic, would love to shrink the NTFS partition as well but thats only on the wish list. 

It took 10 goes to get all the way through the install, strange disk write errors its a dell 4700, builds OK on ide but not on the SATA drive? Always breaks up building the LTSP chroot? tried several media & the media test OK, have had issues with fedora on same machine & drive (strange lockups & file errors) anyway dd if=/dev/zero of=/dev/sda2 sda3 etc  & got all the way throught the 10th install without an error! so as you can imagine i am keen as mustard to find a solution that doesn't involve reinstalling

---

### Post by roelofs on 2006-01-03
You may need to boot from CD for the final step, but yes, you can move (copy) your /usr stuff onto the / partition.  Basically, do something like this:

```
mkdir /usrnew
cd /usr
tar cvf - . | (cd /usrnew; tar xfBp -)
```

Now you have a copy of /usr in /usrnew, which is on the / partition.  The final step is to umount the old /usr, remove the /usr mount point, and move /usrnew to /usr; this is the tricky part since tools like mv, rm, umount, your shell, etc.--or shared libraries on which they depend--might, in principle, live on /usr.  (Normally they live in /bin, however, and they depend only on /lib/libc.so, so it might/"should" work.)  You can always boot Linux from a live CD, however, and mount your / partition on the live system's /mnt (or whatever); at that point, simply

```
rmdir /mnt/usr
mv /mnt/usrnew /mnt/usr
```

...and edit the old /usr out of your fstab (/mnt/etc/fstab) so you don't panic during the next boot.

Even if you do it "live" (i.e., not using a bootable CD), I'd reboot immediately after switching, just to make sure everything's sane.  (Keep a bootable CD around in any case, just in case. ;-) )

---

