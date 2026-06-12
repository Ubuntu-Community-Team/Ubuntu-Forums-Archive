---
title: "Move Ubuntu RAID1 install to new computer"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by narsaw on 2009-09-22
Hello I have a working Ubuntu 9.04 system. It's OS is installed on a RAID 1 array (2 80GB sata drives).

The current system is an AMD Athlon 64

```
Linux myserver 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux 
```

I am getting a new computer very soon. It's a dual core INTEL system. Obviously it will have a new motherboard and processor. 

I am hoping that I can just remove the RAID 1 array disk and just put in the new computer and boot without issues

Is this possible, what complications? Will ubuntu automatically install the motherboard chipset drivers? The motherboard is based on the Intel P965a socket 775 chipset.

mdadm.conf looks like:

```

 mdadm.conf
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
MAILADDR chandersawh@gmail.com

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=374a7db9:0625fdc2:1ddad32f:0a5580cd

# This file was auto-generated on Sat, 16 May 2009 04:28:21 +0000
# by mkconf $Id$

```

---

### Post by narsaw on 2009-09-23
bump

---

### Post by dfishjr on 2009-09-23
I also need help with this procedure.  My system drive crashed and I have had to rebuild.  Installed 9.04 successfully.  Now I have to bring the RAID5 up.  There are 4 disks, one was used for spare.  I do not know how to restore the RAID, so I would be interested in this as well.  I have searched but only found bits of procedures here and there, such as MDADM --ASSEMBLE, but I don't know how to use it.  Or what to do before and after.

Your help would be greatly appreciated.  It would be a life-saver to get the RAID back.

Thanks,
Don Fish Jr.

---

### Post by bgiannes on 2009-10-01
i'm thinking of moving my raid 1 array (data only) /dev/sdc and /dev/sdd to another PC


I was just going to:-

1)backup the data

2)move the HD's

3)Turn on the PC
sudo fdisk -l, note the new dev names

4)Make the mdadm config using the out put from
mdadm --detail --scan --verbose

note:- the part will look like this; devices=/dev/[name],/dev/[name]

the names should be the same from step 3)

5)Make mounting point
mkdir /mnt/Raid1

6)Add the mount to the fstab file
/dev/md0      /mnt/raid1     ext3    defaults    1 2

7)Reboot

Would that work?


BUT:- You have your OS on the raid, so if the dev names are different then you will need to make the corrections to grub.  If you are only dropping the HD's (in the same order, ie /dev/sda will stay as /dev/sda) the new system should just work.  Note: the install is a 64bit, the new CPU and MoBo should be the same

---

