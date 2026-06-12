---
title: "Script for auto-mounting 250GB IDE Slave"
date: 2009-01-20
forum: Hardware
---

### Post by dave.mcdaniel on 2009-01-20
Hi,

My company has made the complete switch from Windows to Ubuntu (which has been an 8 month journey) and things are moving along smoother than we could have imagined with Windows. I am having one little glitch, well not really a glitch more of a pain.  The problem is our file server has two hard drives. The master hard drive is a 40GB Quantum Fireball and the slave is a Western Digital 250GB. The issue is when the machine boots up the Western Digital has to be mounted manually every time.  Is there a script, or something like that that I can program into the OS so when the machine boots up it automatically mounts the drive?

Here are the machine specs:

Intel P-4 1.6 Ghz (Socket 478, single core)
512MB RAM
Quantum 40GB  (Master)
Western Digitial 250GB (Slave)
Western Digital 160GB (External HDD)
Floppy drive
Ubuntu 7.10 (Gibbon 32-bit)
Gnome Desktop

---

### Post by taurus on 2009-01-20
What filesystem is that 250GB drive?  If you want to mount it automatically upon boot, you just need to add an entry in /etc/fstab for it.

Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by dave.mcdaniel on 2009-01-21
the file format on the slave hard drive is Fat 32.

---

### Post by taurus on 2009-01-21
If you are running Ubuntu only, why even use fat32/vfat filesystem for the second harddrive.  Should format it to ext3 which is much better.  However, if you still want to mount that second harddrive, edit /etc/fstab and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   vfat  iocharset=utf8,umask=000  0  0
```
Save it.  Then, create a new mount point and either mount it or reboot.

```
sudo mkdir /media/sdb1
sudo mount -a
-or-
shutdown -r now
```

p.s.  If you want to mount /dev/sdb1 somewhere else besides /media/sdb1, then just replace /media/sdb1 with your new mount point in /etc/fstab.  Make sure that new mount point exists.

---

### Post by dave.mcdaniel on 2009-01-22
Thanks for the information. I will try and edit the etc file.

It was formatted in FAT32 becuase at the time we still had one machine with Windows 2000 on it (and this is before I knew about SAMBA).  Just curious, if i take that drive and place it in an external USB enclosure, won't that accomplish the same thing I'm trying now? Reason why I'm asking is for future refernce if we need to add another slave to the system.

---

