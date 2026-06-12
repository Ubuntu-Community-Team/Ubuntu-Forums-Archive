---
title: "RAID+LVM LTSP install"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by ermeyers on 2009-10-13
I've been reading the various pages on [http://help.ubuntu.com]("http://help.ubuntu.com/") regarding RAID and LVM.

[https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html)

[http://https://help.ubuntu.com/community/Installation#Installing on external or RAID hard disks]("http://https//help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks")

[http://https://help.ubuntu.com/community/Installation/LVMOnRaid]("http://https//help.ubuntu.com/community/Installation/LVMOnRaid")

[http://https://help.ubuntu.com/community/Installation/SoftwareRAID]("http://https//help.ubuntu.com/community/Installation/SoftwareRAID")

[http://https://help.ubuntu.com/community/Installation/RAID1%2BLVM]("http://https//help.ubuntu.com/community/Installation/RAID1%2BLVM")

I want to install Ubuntu LTSP servers with both SW_RAID and LVM.  I have a server named ltsp which has 4 scsi disks /dev/sd[abcd].  Using the LTSP server install selection on the Alternate CD, and selecting *"Guided - use the entire disk and setup LVM"* partitioning, the VG=ltsp, LV=root|swap_1 are created.  I like this basic LVM setup, so I'd like to emulate its LVM organization, when adding RAID to it.
```

root@lts1:~# ls -l /dev/ltsp
total 0
lrwxrwxrwx 1 root root 21 2009-09-11 15:02 root -> /dev/mapper/ltsp-root
lrwxrwxrwx 1 root root 23 2009-09-11 15:02 swap_1 -> /dev/mapper/ltsp-swap_1

```Abbreviated:
```

root@ltsp:~# lshw -C disk                         
  *-cdrom                                                      
       ...
  *-disk:0                                                     
       logical name: /dev/sda                                  
       size: 8683MiB (9105MB)
  *-disk:1
       logical name: /dev/sdb
       size: 8683MiB (9105MB)
  *-disk:2
       logical name: /dev/sdc
       size: 16GiB (18GB)
  *-disk:3
       logical name: /dev/sdd
       size: 8683MiB (9105MB)

```Following the [https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html) RAID section, I partitioned the disks for RAID, as follows:
```

sda   9.1G
   1 pri 452.4 MB K raid (RAID1 active for swap)
   2 pri   8.6 GB K raid (RAID10 active for / part 1)
sdb   9.1 GB
   1 pri 9.1 GB K raid (RAID10 active for / part 2)
sdc 18.2 GB
   1 pri 452.4 MB K raid (RAID1 spare for swap)
   2 pri   8.6 GB K raid (RAID10 spare for / part 1)
sdd   9.1 GB
   1 pri 9.1 GB K raid (RAID10 spare for / part 2)

```The problem that I'm having is that the section "Logical Volume Manager (LVM)" in the page  [https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html) talks about LVM install without RAID.

How do I continue from the RAID into adding LVM?

Thanks,
Eric

---

### Post by dstew on 2009-10-14
I think once you have your RAID set up, you can create a logical volume out of the RAID partitions, just as if they were physical disk partitions. I think you create the RAID first, then the logical volume group out of the RAID, using the **pvcreate** and **vgcreate** commands. You just use RAID partition device names as the arguments. It's been a while since I did this, though, and I could be wrong.

---

### Post by ermeyers on 2009-10-15
I got into it, and saw as you said.  Pretty easy really, once you see it a couple of times.  Please see my thread [http://ubuntuforums.org/showthread.php?t=1292411](http://ubuntuforums.org/showthread.php?t=1292411) .  Thanks.

---

### Post by ermeyers on 2010-09-23
Update [SOLVED] and should be useful for others with multiple disks wanting RAID10-LVM-EXT4 configurations.  I performed Manual Disk Partitioning using the Alternate Install CD.

[B]lts1 Server Hardware:
[/B]* NCR server, 4 Pentium III (i686) 32 bit processors and 2 GB RAM
*** lshw -c CPU
** SCSI disks
*** lshw -c DISK
**** four disks: sd[abd]=9.1GB, sdc=18.2GB

[B]Disk Partitioning Plan for RAID10-LVM-EXT4 Configuration:
[/B]
RAID10 Configuration:

* Active RAID partitions: sd[abd]
* Spare RAID partitions: sdc

* DISKS: sd[abd]=9.1 GB
** Primary [1] 100 MB RAID type FD (boot)
** Logical  [5] 450 MB RAID type FD (swap)
** Logical  [6] 8.6 GB RAID type FD (os)

* DISK sdc=18.2 GB
** Primary [1] 100 MB RAID type FD (boot)
** Logical  [5] 450 MB RAID type FD (swap)
** Logical  [6] 8.6 GB RAID type FD (os)
** Logical  [7] 9.1 GB EXT4 type 83 (extra)

1. RAID10 md0 with LVM VG-LV
** [3] md0-active=sd[abd]1
** [1] md0-spares=sdc1
** vg=lts-boot
** lv=lts-boot-lv
** Format type ext4 and mount as /boot

2. RAID10 md1 with LVM VG-LV
** [3] md1-active=sd[abd]5
** [1] md1-spares=sdc5
** vg=lts-swap
** lv=lts-swap-lv
** Format type swap

3. RAID10 md2 with LVM VG-LV
** [3] md2-active=sd[abd]6
** [1] md2-spares=sdc6
** vg=lts-os
** lv=lts-os-lv
** Format type ext4 and mount as /

---

