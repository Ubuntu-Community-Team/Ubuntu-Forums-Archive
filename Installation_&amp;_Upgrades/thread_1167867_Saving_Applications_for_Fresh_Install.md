---
title: "Saving Applications for Fresh Install"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by CanasClone on 2009-05-23
I run a windows/ubuntu dual boot but my windows partition got corrupted by a virus (imagine that) so I reinstalled windows, unfortunately rewriting the MBR. I thought reinstalling grub would be a simple procedure, but I could not get it to work right and the bootloaders on the ultimate boot cd didn't recognize my ubuntu partition for some reason. Anyway, I was locked out of ubuntu and lived with it until 9.04 was released. Now I want to install 9.04 but it would be a hundred times easier if I could reinstall my previous applications in 9.04 with some simple tricks. I have access with a live cd to all of my ubuntu files on the hard drive but cannot boot directly into it. I've seen tricks for creating a list of installed applications using "dpkg --get-selections > backup" but this requires being booted into ubuntu in the first place. Is there a list somewhere in the filesystem of all of dpkg's installed packages that could work too? Thanks!

---

### Post by albinootje on 2009-05-23
> **CanasClone said:**
> Is there a list somewhere in the filesystem of all of dpkg's installed packages that could work too?

You can boot from the Ubuntu installation cdrom, then find out on 
which partition your Ubuntu installation was. 
Let's assume it was /dev/sda3, then you can use chroot to find out what is installed, for example :
```

sudo mkdir /mnt/sda3
sudo mount /dev/sda3 /mnt/sda3
sudo chroot /mnt/sda3
dpkg --get-selections > /backup.txt
exit
sudo cp /mnt/sda3/backup.txt .
sudo umount /mnt/sda3

```
And then copy or email the backup.txt to somewhere else.

---

