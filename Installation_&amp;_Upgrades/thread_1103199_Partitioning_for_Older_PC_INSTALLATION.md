---
title: "Partitioning for Older PC INSTALLATION"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by jamadacai on 2009-03-22
I have a **Dell Optiplex GX150, 40gb hdd, 512 ram**.

I completely wiped the hard drive (I think) and tried to install Ubuntu.
Everything installs but I get the Grub 1.5 error 18 on start up. 

I have spent hours trying to learn 'How to', tried partitioning, etc but am still getting nowhere.

From what I understand, in BIOS, I have the old config that doesn't recognize the size of my hard drive (overly simplified explanation I suppose). 

To fix this I am supposed to make a /boot partition at the beginning of the hdd partition.
I have actually gone through the partitioning a couple of times (from the  Live cd) and tried various different partitions.

Here's the rub, I am completely new to Linux and to partitioning and have no idea what partitions I am supposed to have. I think I have some of them but have no idea which are supposed to be expandable, etc.
"/" (root?) /boot, /home and some swap one.

Tried all of those combos but it's like flying in the dark. Every HELP site is for dual partitioning but I just want UBUNTU installed.

So, **40gb** hdd, how (in what order) should I **partition** it to get rid of GRUB 18. 

I know you probably get tons of questions about this but Search didn't show any.
Please help, I have spent hours trying to figure this out and I really like UBUNTU (from Live cd tryout). :(

---

### Post by upchucky on 2009-03-22
boot using the live cd, then download this,

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then in the application > accessories > terminal do this

```
sudo bash ~/Desktop/boot_info_script*.sh

```

post the results here.


typically you need 10g partition for ubuntu, half of the available pc ram size for the swap partition, and the rest of drive space for the home partition.

---

### Post by jamadacai on 2009-03-22
Per your instructions.

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

---

### Post by hexanol on 2009-03-22
It looks like your BIOS doesn't have "Enhanced Disk Drive Services". Upgrading your BIOS would be an easy way to solve this problem, but I don't know if there's, first, new BIOS released for your computer and if the new BIOS would actually support EDD.

So, the other solution is to create a small ext3 partition in the first 8GB of your disk who would holds the "boot files".

Note that right now, from your output, it looks like there's no partitions on your hard drive. So, since you have no partition to lose, you would need to install ubuntu this way:

```
1st partition: "/boot" 256 MB
2nd partition: "/" size you want
3rd partition: "swap" maybe 768 MB
```

---

### Post by jamadacai on 2009-03-22
THank you very much. I followed your instructions and still got the GRUB 18 error. I went back into BIOS though and figured out how to fix it. I wouldn't have been able to figure it out without your initial help though.

Cheers.

---

