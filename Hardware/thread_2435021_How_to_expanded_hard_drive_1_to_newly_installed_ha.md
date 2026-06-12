---
title: "How to expanded hard drive 1 to newly installed hard drive 2"
date: 2020-01-15
forum: Hardware
---

### Post by craigjem on 2020-01-15
Hi

As in Windows if I install a new hard drive I can extend the partition to the new hard drive making it larger using Disk Management tool

Initially when I installed Ubuntu I did not create LVM but used the wizard. I have recently installed a new physical dive due to running out of space on the initial disk and wish to extend the partition to the space on the drive but see no simple way of doing it.

I have played with GParted and read other documentation suggesting I should have created a LVM on the initial installation of Ubuntu, **am I forced to reinstall from scratch **or is there some command line or GUI tool which will allow me to expand the partition of disk 1 to disk 2 with reinstalling?

Thank You

---

### Post by CelticWarrior on 2020-01-15
Yes, you need LVM.

---

### Post by jimmyrus on 2020-01-15
> **craigjem said:**
> Hi

As in Windows if I install a new hard drive I can extend the partition to the new hard drive making it larger using Disk Management tool

Initially when I installed Ubuntu I did not create LVM but used the wizard. I have recently installed a new physical dive due to running out of space on the initial disk and wish to extend the partition to the space on the drive but see no simple way of doing it.

I have played with GParted and read other documentation suggesting I should have created a LVM on the initial installation of Ubuntu, **am I forced to reinstall from scratch **or is there some command line or GUI tool which will allow me to expand the partition of disk 1 to disk 2 with reinstalling?

Thank You
Depends on what your doing. If you're just running out of space on your home, you could just format the new drive, copy your home folders over to it and reboot into single user mode. Change your fstab to mount the new drive as /home, and that's all. Could also just move stuff to it, and symlink things like /var to the new drive and you won't have to mess with lvm at all.

lvm is pretty clean though, and lets you get away with a lot. What version of 'buntu are you using? If you're not up to date, may want to consider a fresh install anyway and do it all at once.

---

### Post by craigjem on 2020-01-15
Thanks for your reply, I will probably go ahead and install 19.10 using LVM as running an earlier version of UB...
Just have to allocate a few hours, which is a bit of a pain... I guess in the future it would be better to always use LVM

---

### Post by TheFu on 2020-01-15
While you can use LVM for something like this, spanning file systems across different disks doubles the chances of a single disk failure corrupting all the files on both disks. Not recommended.  If you do decide to do this, please, please, have excellent backups for when a failure happens.  I lost 80% of my data doing this before I got backup religion.

However, any partition can be mounted to any empty directory.  That's extremely powerful, since we can effectively add 1 MB - 10 TB of storage to any specific location that needs it just by moving over files to the new storage file system, then mounting it where needed. The new storage can be a partition+file system or partition+pv+vg+lv+file system, if you like.  I use LVM on physical disks for the added flexibility it provides, but it isn't necessary in this situation.

For example, on a virtual machine server here, I needed extra storage to hold VMs, so I created a 200G LV and mounted it exactly where needed:
```
$ df -hT
Filesystem                        Type  Size  Used Avail Use% Mounted on 
/dev/mapper/hadar--vg-libvirt--lv ext4  197G  2.8G  184G   2% **/var/lib/libvirt**
```

Something like this is commonly done for /home/. For example, on a different machine:
```
$ df -Th 
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root     ext4   25G   15G  8.9G  62% / 
/dev/mapper/ubuntu--vg-home--lv ext4   74G   19G   52G  27% **/home** 
/dev/mapper/ubuntu--vg-stuff    ext4   99G   62G   33G  66% **/stuff**
/dev/sda2                       ext2  721M  186M  499M  28% /boot 
/dev/sda1                       vfat  511M  3.7M  508M   1% /boot/efi
```

I create LVs based on backup needs, since backup and recovery are what drive my storage layout.

---

### Post by triwave on 2020-05-28
> **jimmyrus said:**
> Depends on what your doing. If you're just running out of space on your home, you could just format the new drive, copy your home folders over to it and reboot into single user mode. Change your fstab to mount the new drive as /home, and that's all. Could also just move stuff to it, and symlink things like /var to the new drive and you won't have to mess with lvm at all.

Hi - not trying to hijack thread ... but I was doing exactly same thing and ran into some trouble - looking for some advice where to look to debug and fix.

My 18.04 system was all on a single drive with a separate partition for / and /home

I added a new drive I want to use as /home - so I made an EXT4 partition and copied the user directory to that drive using rsync (actually Grsync GUI) with preserve options for date, permissions, owner ... 

I can mount that drive while still running original system and everything seems intact.

Now I modified fstab to set new drive for /home , reboot , and get stuck at login screen. I am presented with login box and enter password ... then it flashes and goes back to login screen.  I looked at journal log in terminal recovery mode and see an error that goes something like this:

```
mount: /home : wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error
kernel: EXT4-fs (sdc1) : VFS: Can't find ext4 filesystem
Then few more lines all indicating mount process failed and exited with code status=32
```

Since I mount it manually and gparted shows it as EXT4 I guess it's something else? What did I do wrong? Maybe didn't format correctly or superblock issue?

Appreciate any pointers in the right direction ... I'm sure it's something small.

Thanks so much

---

### Post by TheFu on 2020-05-28
triwave, please open your own thread.

---

### Post by triwave on 2020-05-28
Sure thing - it is posted here: [https://ubuntuforums.org/showthread.php?t=2444319]("https://ubuntuforums.org/showthread.php?t=2444319")

Thanks

---

### Post by coffeecat on 2020-05-28
Thread closed.

---

