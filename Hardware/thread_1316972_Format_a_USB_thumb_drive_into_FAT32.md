---
title: "Format a USB thumb drive into FAT32"
date: 2009-11-06
forum: Hardware
---

### Post by w3stfa11 on 2009-11-06
I'd like to know how I can format a USB drive under Ubuntu (command-line only) as FAT32. 

Is mkfs the only command I need? What parameters do I need? Any help is greatly appreciated.

---

### Post by suibhne on 2009-11-06
Any reason for not using gparted? I find it saved me a few times.

oops, forgot to add the instructions via command line:

sudo su

# fdisk -l   (this discovers sdaX)

# umount /dev/sdaX

format device to FAT32

# mkdosfs -F 32 -I /dev/sdaX


Where X is the number from command # fdisk -l


This should work fine

---

### Post by w3stfa11 on 2009-11-06
Thanks suibhne. I need it command-line only because I'll be running it in a script.

---

### Post by suibhne on 2009-11-06
Ah Ok. I was just wondering.

---

### Post by w3stfa11 on 2009-11-06
Nevermind, my mistake. Commands work great. Thanks!

---

