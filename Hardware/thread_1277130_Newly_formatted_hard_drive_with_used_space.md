---
title: "Newly formatted hard drive with used space"
date: 2009-09-27
forum: Hardware
---

### Post by cross157 on 2009-09-27
I formatted a Western Digital external USB connected 320Gb hard drive today to the ext4 format from ntfs. The result is quite mysterious. There is 15.2Gb of used space on the drive per the Properties window, but as you can see in Nautilus nothing is on the drive (Show Hidden Files is checked)

SEE ATTACHMENT

the **dir** command in a terminal when accessing the folder shows nothing.

Can anyone help me figure this out and clear that space 15Gb isn't trivial.

---

### Post by oboedad55 on 2009-09-28
> **cross157 said:**
> I formatted a Western Digital external USB connected 320Gb hard drive today to the ext4 format from ntfs. The result is quite mysterious. There is 15.2Gb of used space on the drive per the Properties window, but as you can see in Nautilus nothing is on the drive (Show Hidden Files is checked)

SEE ATTACHMENT

the **dir** command in a terminal when accessing the folder shows nothing.

Can anyone help me figure this out and clear that space 15Gb isn't trivial.

That seems excessive. Normally the filesystem will take up a few megs, but 15 gigs is too much. Have you tried ext3?

---

### Post by cross157 on 2009-09-28
oboedad55 - at your suggestion I reformatted to ext3, same result. 15 Gb of used space on a fresh reformat.

---

### Post by oboedad55 on 2009-09-28
> **cross157 said:**
> oboedad55 - at your suggestion I reformatted to ext3, same result. 15 Gb of used space on a fresh reformat.

Have you tried reiserfs? I've use that on many Linux installs. It's very stable and fast.

---

### Post by DancingGeek on 2012-11-08
I had this issue, and I found this which allowed me to resolve it:

[https://help.ubuntu.com/community/InstallingANewHardDrive#Modify_Reserved_Space_.28Optional.29](https://help.ubuntu.com/community/InstallingANewHardDrive#Modify_Reserved_Space_.28Optional.29)

It's to do with an automatic 5% being reserved, but you can reduce it to e.g. 1%.

---

### Post by atkrad on 2012-11-08
Hello
Please insert output this command:
```
sudo fdisk -l
```

---

