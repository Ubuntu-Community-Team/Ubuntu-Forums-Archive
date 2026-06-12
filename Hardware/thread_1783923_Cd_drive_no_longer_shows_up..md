---
title: "Cd drive no longer shows up."
date: 2011-06-16
forum: Hardware
---

### Post by ovisobscuris on 2011-06-16
My drive crapped out one day. I was trying out lubuntu and kubuntu on my inspiron b120 running natty and after taking a look around decided to stick with natty. My drive disappeared on me right after. Lord knows what I did.

Stuff that others have been told to do. Hasn't helped too much.
```

ovisobscuris@Lappy:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ovisobscuris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ovisobscuris)

ovisobscuris@Lappy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6f5f16aa-bf09-4720-af85-5984ecbe7e48 none            swap    sw              0       0

ovisobscuris@Lappy:~$ sudo lshw -c disk
[sudo] password for ovisobscuris: 
  *-disk                  
       description: ATA Disk
       product: TOSHIBA MK4026GA
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: PA10
       serial: X5EE5819T
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000373c9
  *-cdrom
       description: DVD reader
       product: CDRW/DVD TSL462C
       vendor: TSSTcorp
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: DE01
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
  *-cdrom
       description: SCSI CD-ROM
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio
       configuration: status=ready



```

SMART status is disabled. Can detect a disk and the size, but still shows nocd when checked. Unless its busy checking out the disk, then status=busy.

Any ideas?

---

### Post by ovisobscuris on 2011-06-17
bumpity

---

### Post by dandnsmith on 2011-06-18
I don't know if this is a version detail thing, but that listing is showing 2 CD devices. Is that correct? If so which are you complaining about, if not can you add any clarification at all?

Normally CD insertion is followed by (1) recognition by the device, which then spins up in an attempt to read the index track (innermost) (2) successful read of the index track, which is passed to the OS for action. It sounds like you pass the first hurdle, but not the 2nd. At this point I'd try different CDs, and possibly a lens-cleaning CD. After that I'd be trying a different CD drive (internal or external) to see whether it could be a software problem.

Comment: I've had drives suddenly fail to read (successfully) CDs - especially when they're just out of warranty period.

later: Just found a posting which might be pertinent:
[here](http://ubuntuforums.org/showthread.php?t=801771)

---

### Post by ovisobscuris on 2011-06-19
I just realized that that second drive was there. I don't have another one, so who knows what that one is. Perhaps an emulated disk? The proper one is most definitely the TSSTcorp one, but from that other post looks like its normal to have two. Thanks for the link, i'm gonna follow up when I get home. Will post details after.

---

