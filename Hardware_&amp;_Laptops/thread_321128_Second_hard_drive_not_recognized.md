---
title: "Second hard drive not recognized"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by aviron on 2006-12-18
I installed a second SATA drive in my existing Ubuntu 6.01 system. Using the Gpartd live CD I was able to create a ext3 filesystem on this drive. When I boot Ubuntu, the new disk is not visible. There are no /dev entries for it. What did I miss? Thanks.

---

### Post by lostelectron on 2006-12-18
I am having the same problem. I am using a dual boot system. WinXp detected the hard drive and I formatted it as NTFS. 

fdisk -l in Kubuntu Edgy did not show anything about the new HDD

---

### Post by lostelectron on 2007-02-09
I have not tried this out yet, but I think if you connect the second hard disk as secondary master, this will work.

---

### Post by taurus on 2007-02-09
Actually, the command should have been

```
sudo fdisk -l
```

---

### Post by tarclee on 2007-02-26
my hd reading error,cant load the ubuntu.i try put it as 2nd harddisk but it did not show out the hd drive icon.the data inside is very important,any1 can help me how to access it?

---

### Post by Tom Tiger on 2007-02-26
> **aviron said:**
> I installed a second SATA drive in my existing Ubuntu 6.01 system. Using the Gpartd live CD I was able to create a ext3 filesystem on this drive. When I boot Ubuntu, the new disk is not visible. There are no /dev entries for it. What did I miss? Thanks.

Look in /etc/fstab,  if it isn't here you will have to either use the mount command sudo mount /dev/sdx /mnt/sdx (x being the sata drive either sdb sdc....)

or add an entry in fstab like
/dev/sdx /mnt/sdx ext3 user,auto,rw,exec,users 0 0

make sure that a directory sdx under /mnt exist, otherwise it won't mount.

Hope this helps.

---

