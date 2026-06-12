---
title: "External HDD doesn't work on inital boot"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by paul_manning22 on 2007-07-29
I have and external HDD that refuses to detect on inital boot up.  If I unplug it and plug it back in once the system has booted, the usb core detects it and assigns it a dev id.  I can then run mount -a and everything works fine.  Considering this machine is a file server of sorts this is a bit of a pain to go through after every reboot.  Anyone got any idea's why this could be happening?  The machine also has one of those 5 in 1 memory card readers and I've sorted through the system log they all detect fine and get dev id's on bootup no worries. I'm stumped.  My apologies if there is already an answer in the forums.  I did hunt around.....

---

### Post by pbcartwright on 2007-07-29
is that drives partition in your /etc/fstab??
what does syslog say after a boot??

---

### Post by paul_manning22 on 2007-07-29
> **pbcartwright said:**
> is that drives partition in your /etc/fstab??

Yes it is, hence the 'mount -a' command working once the device is reset once the system is up.  For reference it always detects as sdd1

> **pbcartwright said:**
> what does syslog say after a boot??

Nothing regarding the drive which is part of the problem.  As I stated, all my other usb flash media detects fine and has dev Id's are created, eg; sdc1 etc.  But the external HDD has nothing!  Then once the system is booted, and the device is reset, all the correct relevant information in the syslog appears.

---

### Post by paul_manning22 on 2007-07-31
Well the plot thickens!  I obviously had a 'man look' through the system log the last couple of times because I have discovered the drive is in fact detecting on boot as sda1.  sdb and sdc (flash media) readers also detect.  I changed my FSTAB to reflect to external hdd's location but I am still having no luck.  It tells me /dev/sda1 is already mounted or my mount point is busy.  I've trying manually mounting to several locations with the same error.  I've tried unmounting and it tells me the drive is not mounted!!! 

Here's the output of the mount command;

> /dev/hda1 on / type reiserfs (rw,notail)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/hdd on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=mythtv)

And here's the syslog refering to the drive detection;

> Aug  1 03:14:44 localhost kernel: [   23.208000] scsi 0:0:0:0: Direct-Access     ST320082 2A               3.01 PQ: 0 ANSI: 0
Aug  1 03:14:44 localhost kernel: [   23.280000] scsi 1:0:0:0: Direct-Access     USB2.0   CF  CardReader        PQ: 0 ANSI: 0
Aug  1 03:14:44 localhost kernel: [   23.284000] scsi 1:0:0:1: Direct-Access     USB2.0   CBO CardReader        PQ: 0 ANSI: 0
Aug  1 03:14:44 localhost kernel: [   23.320000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 19
Aug  1 03:14:44 localhost kernel: [   23.320000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
Aug  1 03:14:44 localhost kernel: [   24.008000] NET: Registered protocol family 10
Aug  1 03:14:44 localhost kernel: [   24.008000] lo: Disabled Privacy Extensions
Aug  1 03:14:44 localhost kernel: [   24.204000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
Aug  1 03:14:44 localhost kernel: [   24.204000] sda: Write Protect is off
Aug  1 03:14:44 localhost kernel: [   24.204000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
Aug  1 03:14:44 localhost kernel: [   24.204000] sda: Write Protect is off
Aug  1 03:14:44 localhost kernel: [   24.204000]  sda: sda1
Aug  1 03:14:44 localhost kernel: [   24.212000] sd 0:0:0:0: Attached scsi disk sda
Aug  1 03:14:44 localhost kernel: [   24.216000] sd 1:0:0:0: Attached scsi removable disk sdb
Aug  1 03:14:44 localhost kernel: [   24.220000] sd 1:0:0:1: Attached scsi removable disk sdc



So it seems when I reset the drive after boot up, it then re-detects as sdd1 and seems happy to work.  Any chance I can force the drive to detect as sdd1 on boot up as a diagnostic?  How would I do that?

---

