---
title: "Second Hard Drive Error"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by ekim1093 on 2009-02-22
Alright, i got a second internal hardrive for my "craptop" (its what i call my xubuntu computer :D) and it is a 40gb one. However in an effort to make both theoriginal and this new harddrive work i ended up installing Xubuntu on both, but much to my dismay that did not work. After some forum searching i eventually discovered that i had to mount the first harddrive in order for it to be useable. So i floowed these instructions and when i went to run the "sudo mount -a" command i got a weird error, 

mount: wribg fs type, bad option, bad superblock  on /dev/sda. missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so

so i tried that command but it didnt help me any.... please help mee

-mike

---

### Post by Pumalite on 2009-02-22
If you want to dual boot with two HH; read this:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by ekim1093 on 2009-02-22
naww i dont want to dual boot, i just want to be able to use bot harddrives for Xubuntu

---

### Post by taurus on 2009-02-22
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

