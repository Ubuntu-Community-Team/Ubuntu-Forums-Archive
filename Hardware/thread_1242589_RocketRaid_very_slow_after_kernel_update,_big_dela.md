---
title: "RocketRaid very slow after kernel update, big delays"
date: 2009-08-17
forum: Hardware
---

### Post by babeliak on 2009-08-17
I did my kernel update on 24th July and since then I have performance issues (huge delays) with my RAID.
First I suspected SAMBA was causing those delays, but today I noticed same poor performance and delays using Nautilus to browse folders on RAID (accessing it locally on Ubuntu machine, NOT over samba/network).

So.. there might be something related to this kernel update..
I will try to recompile RAID driver, maybe it helps, any ideas why my RAID shows poor performance after latest kernel update?
```
~$ uname -a
Linux server 2.6.24-24-generic #1 SMP Fri Jul 24 22:15:50 UTC 2009 x86_64 GNU/Linux
``````
~$ df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb1     ext3     37G  3.2G   32G  10% /
varrun       tmpfs    2.0G 1016K  2.0G   1% /var/run
varlock      tmpfs    2.0G     0  2.0G   0% /var/lock
udev         tmpfs    2.0G   52K  2.0G   1% /dev
devshm       tmpfs    2.0G   12K  2.0G   1% /dev/shm
lrm          tmpfs    2.0G   45M  1.9G   3% /lib/modules/2.6.24-24-generic/volatile
/dev/sda1  fuseblk    932G   83G  849G   9% /mnt/raid
/dev/sda1  fuseblk    932G   83G  849G   9% /media/store
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon     37G  3.2G   32G  10% /home/georg/.gvfs
``````
~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 SCSI storage controller: HighPoint Technologies, Inc. RocketRAID 1740 (rev 02)
```This slideshow in time order is to demonstrate how it is NON functional defacto:
OVER NETWORK (from Ubuntu machine to XP machine)
[ATTACH]125228[/ATTACH]
...
[ATTACH]125229[/ATTACH]
LOCALLY (from RAID to system disk)
[ATTACH]125230[/ATTACH]

[ATTACH]125231[/ATTACH]

[ATTACH]125232[/ATTACH]
Please, could someone point me to the right direction, where to start fix it?
Before kernel update everything worked smoothly since installation.

---

### Post by babeliak on 2009-08-17
I think this is about my situation (quote from ReadMe):
> 4) Driver don't work after a kernel upgrade

   When you update the kernel to a new version, the pre-compiled driver modules 
will no longer work for the new kernel. You have to build new driver for the 
new kernel and update the driver at same time. Remember to make a backup of the 
old kernel and driver in your boot configuration in case the kernel upgrade.

Can someone guide me how to build new driver and update at the same time? I guess I allowed back-up cration during kernel update process, but not sure where to look for files

---

### Post by babeliak on 2009-08-17
SOLVED HERE:
[http://ubuntuforums.org/showthread.php?p=7802074#post7802074](http://ubuntuforums.org/showthread.php?p=7802074#post7802074)

---

