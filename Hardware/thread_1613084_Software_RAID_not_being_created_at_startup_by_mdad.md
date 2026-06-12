---
title: "Software RAID not being created at startup by mdadm"
date: 2010-11-04
forum: Hardware
---

### Post by Gizmonty on 2010-11-04
Hi, I have two 2TB HDDs (/dev/sdb and /dev/sdc) set up as a softraid as /dev/md0 by mdadm. These are mounted at /mnt/raid. This all works fine.

When I restart the computer though the raid is not re-created and I have to do this manually. This is a big problem as the machine is set up as a server without a keyboard or monitor and the startup is halted until a key is pressed to skip the mounting. Once this is done I can quickly recreate and mount the raid with

```
sudo mdadm -A /dev/md0 /dev/sdb /dev/sdc
sudo mount -a
```

My /etc/fstab is as follows

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=10b1abe6-a30d-4507-ab1f-f4f3ef726679 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=8b999e2e-695a-49d3-b5fc-03226afa27e0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3	/mnt/files	ext3	defaults	0	2
/dev/md0	/mnt/raid	xfs	defaults	0	3
```

When I have set up raids with mdadm in the past they have persisted after shutdown and startup. Any ideas why it's not working this time?

---

### Post by Gizmonty on 2010-11-04
Solved it. I didn't have a /etc/mdadm/mdadm.conf file set up. I created it using the following commands

```
echo 'DEVICE /dev/sdb /dev/sdc' > mdadm.conf
mdadm --detail --scan >> mdadm.conf
```

which gave me the file

```
DEVICE /dev/sdb /dev/sdc
ARRAY /dev/md0 level=raid0 num-devices=2 metadata=00.90 UUID=6f7e5152:45287933:6629d78f:a322874e
```

Now it all works

---

### Post by suomaf on 2011-03-06
Hey man,

I am hoping to run a similar setup to you. I have my grub and filesystem stuff in /dev/sda but would like to make /dev/sdb and /dev/sdc to be raid 1. Is there any directions you can help point to for me to try this?

---

