---
title: "Getting rid of Vista of my computer?"
date: 2010-01-06
forum: Hardware
---

### Post by evanp94 on 2010-01-06
Hello, I'm running Ubuntu 9.04 on my Dell Studio 15 (32 bit), with a partitioned hard drive and needed help removing Vista all together, so that Ubuntu is the only operating system in use, with full memory and such. Vista has always given my problems so I want to make a full switch, but when I try to boot in Vista it freezes and I don't know how else to remove Vista outside of it. Help would be greatly appreciated! :)

---

### Post by derekmbarnes on 2010-01-06
May I make a suggestion? Don't remove Windows (even if it is Vista) until you're totally sure everything is working properly in Ubuntu. Case in point: [http://ubuntuforums.org/showthread.php?t=1282161](http://ubuntuforums.org/showthread.php?t=1282161)

---

### Post by x33a on 2010-01-06
> **evanp94 said:**
> so that Ubuntu is the only operating system in use, with full memory and such.

When you are running ubuntu, vista doesn't utilize the memory, so all your system memory is dedicated to ubuntu. though vista is surely taking up a lot of harddisk space.

if you are sure that you want to remove vista, then use gparted to delete your vista partition.

for detailed help, please open a terminal and post the output of
```
sudo fdisk -l
df -h
```

---

### Post by evanp94 on 2010-01-07
Thanks for the help! I'll try that out today.

---

