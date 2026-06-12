---
title: "Failure to mount encrypted RAID5 on boot after 9.04 upgrade (mdadm issue?)"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Aiwa on 2009-04-25
Hi :) I am new to the forum. I hope you guys can help me out with a boot problem after upgrading to Ubuntu 9.04.
 
My fileserver uses a RAID 1 for the boot partition and an encrypted RAID 5 for the root partition. Everything was fine until I upgraded to Ubuntu 9.04. Now the system drops to BusyBox after loading the USB drivers and (correctly) detecting my hard disks.
 
The message I get is this:
 
```

         Check cryptopts=source= bootarg cat /proc/cmdline
         or missing modules, devices: cat /proc/modules ls /dev
-r ALERT! /dev/md1 does not exist. Dropping to a shell!

```
 
In other words, dmcrypt failed to mount my encrypted RAID 5. Turns out /dev/md0 and /dev/md1 (the RAID 1 and RAID 5 respectively) do exist. However, mdadm did not assemble them.
 
```

(initramfs) cat /proc/mdstat
cat: can't open '/proc/mdstat': No such file or directory
(initramfs) mdadm --examine /dev/md0
mdadm: cannot open /dev/md0: No such file or directory
(initramfs) mdadm --examine /dev/md1
mdadm: cannot open /dev/md1: No such file or directory
(initramfs) mdadm --misc -Q /dev/sda1
/dev/sda1: is not an md array
/dev/sda1: device 0 in 4 device undetected raid1 /dev/.tmp.md0.  Use mdadm --examine for more detail.
(initramfs) mdadm --misc -Q /dev/sda2
/dev/sda2: is not an md array
/dev/sda2: device 0 in 4 device undetected raid5 /dev/.tmp.md0.  Use mdadm --examine for more detail.

```
 
mdadm --examine correctly lists all the devices and tells me the RAIDs are healthy. However, I fail to assemble them manually.
 
```

(initramfs) mdadm --assemble /dev/md1 /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2
mdadm: error opening /dev/md1: No such device or address
(initramfs) ls -l /dev/md*
brw-rw----    1 0        6          9,    1 /dev/md1

```
 
What irritates me is that mdadm tells me the RAIDs are healthy when I examine them, but fails to find them on scan.
 
```

(initramfs) mdadm --detail --scan
(initramfs)

```
 
/dev/mdadm.conf does not exist on my initfs so I created one manually just to be sure that is not the issue.
 
```

(initramfs) echo 'DEVICE /dev/sd*[0-9]' > /etc/mdadm.conf
(initramfs) mdadm --detail --scan
(initramfs)

```
 
Nothing. I am out of ideas here. I tried everything I found in wikis and other threads (modprobe md, use --auto=md flag with mdadm etc).
 
Is there something I missed or did I stumble upon a bug? Your help is greatly appreciated.

---

### Post by mmcnett on 2009-04-29
I had a similar problem and noticed that ARRAY lines for two of my three RAID 1 arrays were missing from /etc/mdadm/mdadm.conf after upgrading from 8.10 to 9.04.  After adding them and rebooting, all seems to be working again.  I've attached my /etc/mdadm/mdadm.conf file below.  Note that the ARRAY lines for /dev/md1 and /dev/md2 were missing after upgrading (dev/md0 is my root partition, so perhaps that's why it was still there).  You can get the UUIDs for the arrays with 'mdadm --examine' on any of the disks in the array (E.g. mdadm --examine /dev/sdc1 where /dev/sdc1 and /dev/sdd1 are the array members).  Hope this helps.

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=e34d47c9:74e01ab1:b7d61ceb:1c916dcf

ARRAY /dev/md1 level=raid1 num-devices=2 UUID=004ef8ec:e3e452a2:3523c5f2:de0b4cc6

ARRAY /dev/md2 level=raid1 num-devices=2 UUID=73d92d6e:b8d3dbd1:35d3c5f2:de0b4cc6
```

---

### Post by Aiwa on 2009-04-30
Thanks for the tip mmcnett. I just fixed the problem, but it had nothing to do with the mdadm.conf file.
 
I booted the machine with a live CD, assembled and mounted the raid manually, and found that the mdadm.conf file was okay.
 
In the original post I did not mention that the 2.6.28 kernel of Ubuntu 9.04 did not boot at all (it gets stuck after detecting USB devices). I could only get into the BusyBox of the old 2.6.27 kernel, but from there I could not assemble the RAID, as described.
 
At first I did not think it would be because of lack of modules (after all, the machine used to boot just fine with that kernel), but then I added raid1 and raid456 to /etc/initrams-tools/modules just to be sure.
 
I did update-initramfs for the 2.6.27 kernel and rebooted, and it worked :) Apparently Ubuntu 9.04 requires these modules to be explicitly included while 8.10 did not and the installer did not check for that.
 
So the machine boots again. Unfortunately the network interface seems broken, but that's a different story...

---

### Post by timefortea on 2009-05-08
Hi,
I had the same problem on a fresh install of 9.04 64bit, with an unencrypted RAID 5 array - mmcnett's solution seems to fix it, thanks for the tip!

---

