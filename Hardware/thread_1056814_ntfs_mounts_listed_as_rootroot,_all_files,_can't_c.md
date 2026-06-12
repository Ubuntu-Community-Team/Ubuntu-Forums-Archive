---
title: "ntfs mounts listed as root:root, all files, can't change"
date: 2009-02-01
forum: Hardware
---

### Post by bulwynkl on 2009-02-01
Hi all,

I had a system crash yesterday. On reboot, my ntfs mount refused to stream media...  I had a look at the shared drive permissions (was using samba) and the drive was owned and grouped root:root.  tried all manner of fixes, check disk using external boot disks, etc.

system: ubuntu 8.10, 64bit on dual core PC
bulwynkl@sol:~$ uname -a
Linux sol 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
HDD is samsung 750GB w/- 580GB used.
bulwynkl@sol:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             285G   48G  223G  18% /
...snip...
/dev/sdc1             694G  507G  159G  77% /home
/dev/sdb2             699G  556G  144G  80% /data


what I've tried: many variants of:
sudo chmod 6777 /data
sudo chown 1000:1000 /data

it shows the change being made but without effect on the file system

I've tried unmounting and remounting, specifying -o rw, etc.

I've tried copying a file off the drive (OK), changing owner and permissions (ok) and copying it back, both as root (owner changed to root:root spontaneously) and as bulwynkl (owner changed to root:root spontaneously). 

every single file on the disk is UID and GID 0, except links.

This shows that the drive is writable but that for some reason it is not storing or overwriting uid and gid sttings.

I've just mounted a friends external ntfs 1TB drive (via usb2) with the intention of copying everything over, reformating the drive and copying back - and noticed that the externally mounted drive is all listed as uid:gid root too. it initially refused to mount due to the partition being marked as in use so I had to force mount it - but this did not happen with the local drive...


any suggestions? this is driving me nuts!

---

