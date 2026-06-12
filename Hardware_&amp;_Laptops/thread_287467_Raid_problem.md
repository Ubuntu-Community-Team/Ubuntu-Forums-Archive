---
title: "Raid problem"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by nrgy on 2006-10-28
After I setup a raid with mdadm, mount the raid, and edit fstab if i reboot I get a cannot read superblock error on boot. When I skip the error and try to mount the raid its a no go. MDADM says the raid has no superblock after a reboot and I have no clue what is going on.

The boot error is

sck.ext3: Invalid argument while trying to open /dev/md0

/dev/md0: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

I setup my mdadm.conf

DEVICES /dev/hda /dev/hdb
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=d95ad6c2:820a58d3:f322b6fc:61260e34
   devices=/dev/sda5,/dev/sdd5

fstab is

/dev/md0        /raid     ext3 defaults       0       1
/dev/hdd6       /         ext3 defaults,errors=remount-ro 0 1

At this point its geting realy frustrating whats going on.  I create a raid to only lose it on a reboot.  Ive browsed google to death and these forums finding problems closely related but none with a final solution :/

Thanks in advance.

---

### Post by merovingian on 2007-01-30
I got the same problem here ...

4 drives in RAID 0 connected to a RAID promise card (fastrakk 66)
If I reboot I loose the array.

The only work around I found so far is:

sudo mdadm --stop --scan
sudo mdadm -A /dev/md0
then remount the drive.

I did tried to browse Google without any sucess. 

It is like some process start scanning the drives then becomes unavailable ... weird.



Merv.

---

### Post by sgla1 on 2007-11-14
Take a look at the notes on this page.  Some changes in the latest version of mdadm may be the cause of your problems--we have seen similar issues where I work.
[http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Software_RAID#Misc_RAID_stuff]("http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Software_RAID#Misc_RAID_stuff")

---

