---
title: "Installation virtualization"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by ermeyers on 2009-10-15
I posted this at the new Virtualization forum at LinuxQuestions.org, and I'm posting it here for Ubuntu purposes.

I just loaded VirtualBox on Ubuntu 9.04 to try it out.  Pretty good stuff.[IMG]http://e1h7.simplecdn.net/lqcdn/images/questions/images/smilies/smile.gif[/IMG]

I've been trying to learn more about partitioning disks with RAID, LVM and Encryption, and getting no help from these forums.

I think that the virtualization programs like Virtualbox could really help all of us out in creating better Wiki documentation of the various installation procedures. We don't often get to see a lot of graphical representations of the Text-based debian installer, used on the Ubuntu Alternate disk, and having some snapshots of the installation steps in help.ubuntu.com and ubuntuforums.org would be really CLEAR and helpful.

If Virtualbox would allow me to define disks beyond what I found was IDE Primary Master, IDE Primary Slave, IDE Secondary Slave, then some examples of the complex RAID, LVM and Encryption configs could be documented and run in VirtualBox. We could easily develop complex kickstart and preseed installation scripts without being tied directly to the keyboard and monitor of the target machine.

---

### Post by ermeyers on 2010-09-23
[SOLVED]  Using QEMU (apt-get install qemu).

4 SCSI Disks: sd[abd]=9.1GB, sdc=18.2GB

RAID10+LVM+EXT4 Partitioning plan:

> 
[LIST]
[*] Active RAID partitions: sd[abd]
[*] Spare RAID partitions: sdc
[/LIST]
 
[LIST]
[*] sd[abd]=9.1 GB
[LIST]
[*] P [1] 100 MB RAID type FD (boot)
[*] L [5] 450 MB RAID type FD (swap)
[*] L [6] 8.6 GB RAID type FD (os)
[/LIST]
 
[/LIST]
 
[LIST]
[*] sdc=18.2 GB
[LIST]
[*] P [1] 100 MB RAID type FD (boot)
[*] L [5] 450 MB RAID type FD (swap)
[*] L [6] 8.6 GB RAID type FD (os)
[*] L [7] 9.1 GB EXT4 type 83 (extra)
[/LIST]
 
[/LIST]
 
[LIST]
[*] md0 RAID10+VG-LV
[LIST]
[*] [3] md0-active=sd[abd]1
[*] [1] md0-spares=sdc1
[*] vg=lts-boot
[*] lv=lts-boot-lv
[*] Format type ext4 and mount as /boot
[/LIST]
 
[/LIST]
 
[LIST]
[*] md1 RAID10+VG-LV
[LIST]
[*] [3] md1-active=sd[abd]5
[*] [1] md1-spares=sdc5
[*] vg=lts-swap
[*] lv=lts-swap-lv
[*] Format type swap
[/LIST]
 
[/LIST]
 
[LIST]
[*] md2 RAID10+VG-LV
[LIST]
[*] [3] md2-active=sd[abd]6
[*] [1] md2-spares=sdc6
[*] vg=lts-os
[*] lv=lts-os-lv
[*] Format type ext4 and mount as /
[/LIST]
 
[/LIST]
Create disk images of type qcow2:
```

qemu-img create -f qcow2 sda_9r1GB.qcow2 9.1G
qemu-img create -f qcow2 sdb_9r1GB.qcow2 9.1G
qemu-img create -f qcow2 sdc_18r2GB.qcow2 18.2G
qemu-img create -f qcow2 sdd_9r1GB.qcow2 9.1G

```Using ~/Downloads/xubuntu-10.04-alternate-i386.iso as cdrom:
```

qemu -m 256 -drive file=sda_9r1GB.qcow2,if=scsi,bus=0,unit=0 -drive file=sdb_9r1GB.qcow2,if=scsi,bus=0,unit=3 -drive file=sdc_18r2GB.qcow2,if=scsi,bus=0,unit=4 -drive file=sdd_9r1GB.qcow2,if=scsi,bus=0,unit=5 -boot d -cdrom ~/Downloads/xubuntu-10.04-alternate-i386.iso -soundhw ac97 -net nic -net user

```F4 Modes: "Install an LTSP Server"

Eventually getting into the manual partitioning plan of RAID type FD:
With 100 MB for /boot, 450 MB for swap and 8.6 GB for os / on each disk.

---

