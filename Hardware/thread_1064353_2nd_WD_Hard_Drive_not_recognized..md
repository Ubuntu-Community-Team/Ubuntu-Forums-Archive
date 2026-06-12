---
title: "2nd WD Hard Drive not recognized."
date: 2009-02-08
forum: Hardware
---

### Post by theross12 on 2009-02-08
New here, I'm running newest version of Ubuntu. I have my factory 30GB hard drive that is recognized in Ubuntu. My question is can anyone help me figure out why Ubuntu wont recognize my 2nd internal 120GB Western Digital Hard Drive... Windows recognizes it perfect, so I know everything is wired properly. I would like to have this hard drive accessable because I have close to 50gb of music/video on my 2nd drive. Any help is much appreciated. Thanks

---

### Post by taurus on 2009-02-08
You probably just need to add an entry in /etc/fstab to have it mount automatically each time you boot Ubuntu.

Is it a ntfs filesystem?

Open a terminal and install ntfs-config.  Then, use it to configure your second harddrive, assuming it's ntfs filesystem.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

If not sure, post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

