---
title: "booting raid 5"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by perler on 2006-01-28
hi,

as i learned that it is not possible to boot directly from a raid5 system i think about alternatives.

because i don't want to "waste" two additional disks for a raid1 (mirroring) boot array i thought about this config:

1. 4 disks with 2 partitions each
2. one partition on each disk gets into a raid1 (mirror with 4 disks) which holds /, /boot, /lib, /usr
3. the other partition on each disk gets into a raid5 and will hold the rest (/var, /home etc..)

this way in the case of failure of one disk i still should be able to have a bootable system and the raid5 is degraded but has still all the data.

is there a mistake in my thinking?

PAT

[edited typo]

---

### Post by perler on 2006-01-29
answering myself.. ;)

i did some experimenting in vmware with the setup described in my first post and so far i'm very satisfied with this solution. what i'm not so satisfied with is, that the installer, although definitely able to do the installation had some nasty bugs which i didn't explore to far but which i will mention here anyway:

but first how my raid solution looks like in the end:

4 sata disks (/dev/sda..sdd)

layout of the partitions:

/dev/sdX1 64 MB (yes, M ;) ) mounted to /boot
/dev/sdX2 lotsof GB (for everything else)

/dev/sda1 to /dev/sdd1 are in /dev/md0 as RAID1 (mirror)
/dev/sda2 to /dev/sdd2 are in /dev/md1 as RAID5

/dev/md0 is ext2 and is booted from
/dev/md1 is in LVM group vg1

vg1 has logical volumes for root (/), /srv, /var, /home, /tmp, /swap mounted accordingly

all partitions beside swap are xfs formated (not neccessary.. ext3 is fine)

boot manager is grub

what is not working:

1. everything RAID5 - no boot manager can boot from it
2. (strangely) the RAID1 on md1 

my first installation attempt failed. at the end of the installation, lilo was choosen by the installer but couldn't create a boot record on /dev/md0 nor (by hand) on /dev/sda thru /dev/sdd.

when i started the installation over i deleted the small partitions and recreated them, rebuilt the raid /dev/md0 and suddenly, strangely, not understandably ;)  the ubuntu installer chose grub as a boot manager and successfully installed a boot record on /dev/sda, reboot, done. :)

it may be, that i tried to create the boot raid on /dev/md1 initially, but the ubuntu installer offered me to install the boot record on /dev/md0. i didn't try to force it to /dev/md1 by hand - in the end just avoid putting it somewhere else then /dev/md0.

because the boot record was only put on the first disk in the system i had to put it on to the other disks by hand:

```

#grub
device (hd0) /dev/sdb
root (hd0,0)
setup (hd0)
device (hd0) /dev/sdc
root (hd0,0)
setup (hd0)
device (hd0) /dev/sde
root (hd0,0)
setup (hd0)

```

(it would be enough to put it onto /dev/sdb because when more then one disk is failing at a time the raid 5 is f'up and suicide is the only solution anyway.. but i like symmetry)

so, the raid was booting and running perfectly but then i removed one of the four disks from the vmware session. the session booted but hung at the evms start ("Enterprise Volume Manager..") which seems to be a known bug. somehow evms mounts the parts of the raid it found in wrong order. so, after installation do a```
chmod a-x /etc/init.d/evms
```not to elegant but works.

so, after removal of one of the disks and adding a new one i did a resync and everything is now again in full health.

next step is of course to repeat the installation on a real system but i don't expect any nasty surprsies..

PAT

---

