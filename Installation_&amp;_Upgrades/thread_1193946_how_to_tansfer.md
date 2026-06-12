---
title: "how to tansfer"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by jackson9458 on 2009-06-22
i just bought a new harddrive and i was wondering if there was anyway to copy everything over from the old hard drive to the new one. so when i turn the computer on it boots up to ubuntu as normal as if i still had the old hard drive in. thanks

---

### Post by Herman on 2009-06-22
I would plug both hard disks into the computer and boot from a Live CD operating system or an operating system installed in a USB flash memory stick or in another hard disk.

Then I would use a partition editor like GParted (Gnome Partition Editor), to check which disc is called 'sda', and which one is 'sdb'.

If the one with the operating system and data in it is 'sda', and providing your new hard disk is equal size or larger than your old one, I would run the following command,
```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror
```[COLOR=Red]CAUTION: Be very careful with the 'dd' command, if you accidentally run it backwards and copy the blank disc to the one with the data you will erase all your data![/COLOR]
So double check and check again before running the command.

Regards, Herman :)

---

### Post by jackson9458 on 2009-06-24
thanks. i didnt end up doing it. there wasnt much stuff i needed when i looked

---

