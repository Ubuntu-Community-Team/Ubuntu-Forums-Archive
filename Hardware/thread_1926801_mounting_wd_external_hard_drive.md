---
title: "mounting wd external hard drive"
date: 2012-02-16
forum: Hardware
---

### Post by aydinahmed on 2012-02-16
I have a western digital external hard drive I use to store all my music. I had it on my Windows machine but now I want it on my Ubuntu laptop. When I plug it in No music shows up. I went to terminal and entered df.
This is what it gave me:




Filesystem           1K-blocks      Used Available Use% Mounted on /dev/sda1             73719016   4895040  65079208   7% / none                    991940       256    991684   1% /dev none                    997540       588    996952   1% /dev/shm none                    997540       100    997440   1% /var/run none                    997540         0    997540   0% /var/lock none                  73719016   4895040  65079208   7% /var/lib/ureadahead/debugfs /dev/sr1                629128    629128         0 100% /media/WD SmartWare 

Then I created a dir:
sudo mkdir /media/western
 sudo mount ntfs /dev/sdb1 /media/western 


And this is what it shows:
Usage: mount -V                 : print version        mount -h                 : print this help        mount                    : list mounted filesystems        mount -l                 : idem, including volume labels So far the informational part. Next the mounting. The command is `mount [-t fstype] something somewhere'. Details found in /etc/fstab may be omitted.        mount -a [-t|-O] ...     : mount all stuff from /etc/fstab        mount device             : mount device at the known place        mount directory          : mount known device here        mount -t type dev dir    : ordinary mount command Note that one does not really mount a device, one mounts a filesystem (of the given type) found on the device. One can also mount an already visible directory tree elsewhere:        mount --bind olddir newdir or move a subtree:        mount --move olddir newdir One can change the type of mount containing the directory dir:        mount --make-shared dir        mount --make-slave dir        mount --make-private dir        mount --make-unbindable dir One can change the type of all the mounts in a mount subtree containing the directory dir:        mount --make-rshared dir        mount --make-rslave dir        mount --make-rprivate dir        mount --make-runbindable dir A device can be given by name, say /dev/hda1 or /dev/cdrom, or by label, using  -L label  or by uuid, using  -U uuid . Other options: [-nfFrsvw] [-o options] [-p passwdfd]


.So now my question is this. I am almost sure the wd hard drive is in nfts. Do I have to reformat this drive into another file structure for Ubuntu to recognize it? Will it erase all my music? How can I keep all my music and use with Ubuntu?

---

### Post by ahallubuntu on 2012-02-16
Could be FAT32 not NTFS.

Try this:

sudo fdisk -l /dev/sdb

(assuming WD ext drive is only other drive plugged in besides laptop drive.)

What's the output?

Have you tried simply mounting the drive from the Places menu?  Or just mount it without the "ntfs" and let the mount command figure out the format?

---

### Post by aydinahmed on 2012-02-17
I just realized there is a unlock.exe I can see on the drive. I assume it's locked cause I haven't used it in a while. Suppose there is no way to run unlock.exe is there? Anyway of unlocking it besides hooking it up to a windows machine?

---

### Post by leclerc65 on 2012-02-17
Why don't you install and run 'ntfs-config'.
By the way I delete all the software that come with the external HDD's that I buy.

---

### Post by Grisk13 on 2012-02-17
I tend to agree with Lecerc65 on this, I always clear the nonsense bloatware, it's too easy to screw it up.  

Worst case scenario, you shouldn't have lost use of the drive, you can always reformat the drive.  Does the drive itself show up in your filebrowser when plugged in?

---

