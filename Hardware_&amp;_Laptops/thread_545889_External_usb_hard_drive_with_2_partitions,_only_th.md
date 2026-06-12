---
title: "External usb hard drive with 2 partitions, only the first mounted"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by kirys on 2007-09-08
I have an HD on usb with 2 partitions the first is a fat32 (for sharing files with friends) and the second is an ext3 partition for my backup purposes.
Since latets update (yesterday) after a month without updates (due to connectivity problems), kubuntu 7 only mounts the first partition (fat32) and not mount the second one anymore (before the upgrade everything worked just fine).
I've triend checking the linux partition and e2fsck says everything is ok
What can it be?
Thank you
Kirys

---

### Post by x64Jimbo on 2007-09-08
Will it mount manually with the mount command?

---

### Post by kirys on 2007-09-08
sure it mounts manually (i'm using it this way now).
and the file system is ok (no error detected by e2fsck) and no reading errors, so the hw is fine.

---

### Post by merlinus on 2007-09-08
Post results of:

```

sudo fdisk -l
cat /etc/fstab

```

and indicate which partitions you are referring to.

-merlin

---

### Post by kirys on 2007-09-08
Here we go:

fdisk output :
```

fdisk -l /dev/sdb

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12159    97667136    c  W95 FAT32 (LBA)
/dev/sdb2           12160       30401   146528865   83  Linux

```

fstab content

```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5b7ed0f5-e988-4e20-ab69-1a96dc7c847e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=32e05445-25ee-4c17-a898-22168e28900a /home           ext3    defaults        0       2
# /dev/sda1
UUID=CEAC0F37AC0F199B /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=4e85ecf9-d41f-4b2a-aa06-4e54e921fb1c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

dmesg (you didn't ask for it but maybe is usefull :P)
```

[ 7405.336000] usb 4-3.3.3: new high speed USB device using ehci_hcd and address 6
[ 7405.428000] usb 4-3.3.3: configuration #1 chosen from 1 choice
[ 7405.428000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 7405.428000] usb-storage: device found at 6
[ 7405.428000] usb-storage: waiting for device to settle before scanning
[ 7408.680000] DROPPED IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:02:84:62:48:08:00 SRC=192.168.0.1 DST=192.168.0.255 LEN=177 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=157
[ 7410.428000] usb-storage: device scan complete
[ 7410.448000] scsi 3:0:0:0: Direct-Access     SAMSUNG  SP2514N          0811 PQ: 0 ANSI: 0
[ 7410.448000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[ 7410.452000] sdb: test WP failed, assume Write Enabled
[ 7410.452000] sdb: assuming drive cache: write through
[ 7410.452000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[ 7410.456000] sdb: test WP failed, assume Write Enabled
[ 7410.456000] sdb: assuming drive cache: write through
[ 7410.456000]  sdb: sdb1 sdb2
[ 7410.464000] sd 3:0:0:0: Attached scsi disk sdb
[ 7410.464000] sd 3:0:0:0: Attached scsi generic sg2 type 0

```

This is the output just after the icon of sda1 showed on the desktop
**the missing drive is sdb2**
Cya

---

### Post by Endolith on 2007-11-08
> **merlinus said:**
> Post results of:

```

sudo fdisk -l
cat /etc/fstab

```

and indicate which partitions you are referring to.


Auto-mounting of USB drives is not done with fstab, is it?

---

### Post by x64Jimbo on 2007-11-10
> **Endolith said:**
> Auto-mounting of USB drives is not done with fstab, is it?
It is. That's why there is an "automount" option in fstab that can be turned on/off.

---

### Post by Endolith on 2007-11-10
> **x64Jimbo said:**
> It is. That's why there is an "automount" option in fstab that can be turned on/off.

Auto-mounting of external USB drives that the computer has never seen before is controlled by /etc/fstab?  Really?

It's not controlled by hotplug/automount and based on the partition's label?

---

### Post by x64Jimbo on 2007-11-12
No, not if the computer hasn't seen them before. I have several USB drives defined in my /etc/fstab to automount. But I have to define them myself. Automounting of previously unseen drives is handled by hotplug as you said. I should have been more specific and said "It is if you set it up that way."

---

### Post by Endolith on 2007-11-12
> **x64Jimbo said:**
> No, not if the computer hasn't seen them before. I have several USB drives defined in my /etc/fstab to automount. But I have to define them myself.

That's what I thought.  So we need to fix hotplug, and not just brute force it with fstab.  :-)

---

### Post by x64Jimbo on 2007-11-12
I fear that adding an entry to fstab may be the only way to fix it, unless you have an answer to why hotplug would randomly decide to just stop mounting a certain partition.

---

### Post by Endolith on 2007-11-12
> **x64Jimbo said:**
> I fear that adding an entry to fstab may be the only way to fix it, unless you have an answer to why hotplug would randomly decide to just stop mounting a certain partition.

Well, obviously this thread is supposed to find that answer, not just a kludgy workaround.  :-)

For me, the problem didn't start until Feisty upgrade, which should make it easier to track down the change that broke it.  [http://ubuntuforums.org/showthread.php?t=608210](http://ubuntuforums.org/showthread.php?t=608210)  I wish someone could just tell me what system messages to look for, etc. to troubleshoot it.  I have no idea how hotplug works.

---

### Post by x64Jimbo on 2007-11-12
I guess when someone asks how to fix a problem on the user side, I try to come up with a solution or workaround. It may not fix the problem at its core, but then again, the question of how to fix hotplug is more of one that should be asked of the developers via the bugtracker. If someone here has the answer, great... but the majority of users don't have knowledge of the inner workings of hotplug, myself included. The OP was looking for a solution, but wasn't as specific as you were in your thread. Were this your thread, I probably would not have responded.

---

### Post by Endolith on 2007-11-16
> **x64Jimbo said:**
> I guess when someone asks how to fix a problem on the user side, I try to come up with a solution or workaround. It may not fix the problem at its core, but then again, the question of how to fix hotplug is more of one that should be asked of the developers via the bugtracker. If someone here has the answer, great... but the majority of users don't have knowledge of the inner workings of hotplug, myself included. The OP was looking for a solution, but wasn't as specific as you were in your thread. Were this your thread, I probably would not have responded.

Found this: [https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices)

Will be trying it tomorrow.

---

