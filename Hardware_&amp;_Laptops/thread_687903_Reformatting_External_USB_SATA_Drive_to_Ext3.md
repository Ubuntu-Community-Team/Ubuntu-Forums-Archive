---
title: "Reformatting External USB SATA Drive to Ext3"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by jrc on 2008-02-04
I'm trying to transfer files from my old PC to my new PC.  The old PC has two hard drives:  one is Windows ME and the other is Ubuntu 6.06 LTS (Dapper Drake).  The new PC is a Dell with preloaded Ubuntu 7.10.  My boss gave me a SATA USB external hard drive (formatted for NTFS) with the thought that I could use it to transfer files from the old PC to the new PC. 

When I plug the external hard drive into the old PC, Dapper Drake recognizes it, but I can't copy files to it.  I get a message that it's a read-only drive.  In addition, I suppose it would be problemmatic to copy my FAT32 files from the Windows ME drive to an NTFS drive.  So I thought, "well, I'll reformat the external drive from NTFS to ext3."  But I can't seem to get access to the external drive to reformat it.  When I open GParted and select the external drive (/dev/sda1) and then right-click on it so I can unmount it I get the message "Could not unmount /dev/sda1; No such file or directory."  I'm trying to unmount the external drive because I read in the Ubuntu forums that that is what I must do to start the reformat process.

So can anyone tell me (1) how to get access to this SATA USB external hard drive so I can reformat it, and (2) whether this is the most efficient way to do what I'm trying to accomplish or whether I should go about this in an entirely different way?  Thanks.

JRC

---

### Post by logos34 on 2008-02-04
try 

sudo mkfs.ext3 /dev/sda1

or 

sudo mke2fs -j /dev/sda1

to reformat as ext3.

Or[ install ntfs-3g in Dapper so you can write to it]("https://help.ubuntu.com/community/MountingWindowsPartitions").

---

### Post by jrc on 2008-02-05
Thanks for the quick feedback.

Pardon my cluelessness, but when I enter the command:

 **sudo mkfs.ext3 /dev/sda1**

I get back the message:

 /dev/sda1 is mounted; will not make a filesystem here!

Do I "umount /dev/sda1" or do I umount something in the media directory?  I tried issuing this command:  "umount /media/200 GB_USB (SATA) Drive" but I got this error message:  

bash: syntax error near unexpected token `('

So could you tell me what to do next?  Thanks.

---

### Post by logos34 on 2008-02-05
post the output from the following commands:

**sudo fdisk -l**

and

**mount**

---

### Post by jrc on 2008-02-05
Here's the output for fdisk -l:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24322   195358720    7  HPFS/NTFS

and here's the output for mount:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-51-386/volatile type tmpfs (rw)
/dev/hdb1 on /media/windows type vfat (rw,umask=0000)
/dev/sda1 on /media/200 GB_USB (SATA) Drive type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)

---

### Post by logos34 on 2008-02-05
the gaps in the mount name is causing the syntax errror:

try

sudo umount /media/"200 GB_USB (SATA) Drive"

---

### Post by jrc on 2008-02-05
That did the trick.  Thanks, logos34.

---

