---
title: "Can't mount internal hard disks Ubuntu 12.04"
date: 2012-08-31
forum: Hardware
---

### Post by grove001 on 2012-08-31
I'm running Ubuntu 12.04 and am fairly new to it.  My machine has 3 hard disks, 1 (ext4) 2.0 TB for Ubuntu and home directories, 1 (ext4) 1.5 TB to be used presently when I relocate all /home/ directories for the whole /home/ tree, and a third drive for backup (ext4, 1.0TB).  The machine picked right up on the first disk, did the Ubuntu install, etc.  1.5TB and 1.0TB disks are shown at upper end of directory tree when I use the built-in directory tree traverser (icon is a couple of folders, don't know program's name).  Yet when I try to mount either disk 2 or disk 3 by right cliking them and picking "mount" they won't do it.  If I use fstab to automount them with lines at the end of the file like:
UUID=long--string-here, gotten by blkid /media/ ...
the machine during boot says there's a problem mounting the drive, and asks if I want to skip it.

I also tried using "mount" to mount the disks, but with no more success.

I also have similar problem with external 1TB drive, but it's NTFS.

Any helpful guidance would be much appreciated.

---

### Post by drmrgd on 2012-08-31
Would you mind posting the contents of your fstab file along with the results of the following two commmands:

```
sudo blkid; ls -l /media/
```

That will help to determine the mount data is correctly configured in fstab.

---

### Post by grove001 on 2012-08-31
Output of sudo blkid:
[sudo] password for wmg: 
/dev/sda1: UUID="7f3d522a-dfa3-45f6-b831-1b933901284e" TYPE="ext4" 
/dev/sda5: UUID="01573ec3-c61e-42d0-96ea-789af673ea4f" TYPE="swap" 
/dev/sdb1: LABEL="2nd_drive" UUID="b98c2b87-209c-4bc3-b144-f892e8c0feed" TYPE="ext4" 
/dev/sdc1: LABEL="3rd_disk" UUID="99d6d64d-16d3-40ba-9082-e347280cb8a7" TYPE="ext4" 
/dev/sdd1: LABEL="Lexar" UUID="7CE8C832E8C7E88A" TYPE="ntfs" 

Output of ls -l /media:
total 16
drwxr-xr-x 2 root root 4096 Aug 30 21:20 2nd_disk
drwxr-xr-x 2 root root 4096 Aug 29 14:43 3rd_disk
drwx------ 1 wmg  wmg  8192 Aug 29 12:22 Lexar

Contents of my /etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                           <mount point>   <type>  <options>           <dump>  <pass>
proc                                      /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7f3d522a-dfa3-45f6-b831-1b933901284e /               ext4    errors=remount-ro   0       1
/dev/sda/media/2nd_disk was on /dev/sdb1 during installation
# UUID=b98c2b87-209c-4bc3-b144-f892e8c0feed /media/2nd_disk ext4                        0       2
# /dev/sda/media/3rd_disk was on /dev/sdc1 during installation
UUID=99d6d64d-16d3-40ba-9082-e347280cb8a7 /media/3rd_disk ext4    defaults            0       2
# swap was on /dev/sda5 during installation
UUID=01573ec3-c61e-42d0-96ea-789af673ea4f none            swap    sw                  0       0

Note that the last text line in fstab ends with an EOL character.

Regards,
Will Grove

---

### Post by oldfred on 2012-08-31
You have comment uncommented and the mount commented. And on the first you are missing the default.

> [COLOR=Red]#[/COLOR]/dev/sda/media/2nd_disk was on /dev/sdb1 during installation
[COLOR=Red]# [/COLOR]UUID=b98c2b87-209c-4bc3-b144-f892e8c0feed /media/2nd_disk ext4 [COLOR=Red]defaults                        [/COLOR]0       2
# /dev/sda/media/3rd_disk was on /dev/sdc1 during installation
UUID=99d6d64d-16d3-40ba-9082-e347280cb8a7 /media/3rd_disk ext4    defaults            0       2


Add first red #, remove second red # and add the defaults.
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

run this to see if you get any errors. If it just returns then it is ok.

sudo mount -a

---

