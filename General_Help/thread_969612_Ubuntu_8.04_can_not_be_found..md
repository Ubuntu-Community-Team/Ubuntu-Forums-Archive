---
title: "Ubuntu 8.04 can not be found."
date: 2008-11-03
forum: General Help
---

### Post by JohnParker on 2008-11-03
I tried to make a partition and install windows xp with a dual boot the other day, but XP could not find the partition, so I just restarted without the disk. But I get an error message like operating system can not be found. I'm using the ubuntu live cd right now, I have the grub boot loader. How can I get my computer to detect ubuntu again?

---

### Post by taurus on 2008-11-03
You didn't happen to delete Ubuntu while you tried to reinstall windows, did you?  From the LiveCD, open a terminal and see what happens to your harddrive.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by JohnParker on 2008-11-03
No, I did not. I can see the files when I mount the drive on the live cd.

           Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43924392

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       21048   169068028+  83  Linux
/dev/sda3           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by taurus on 2008-11-03
Okay, mount the partition where / is, /dev/sda1.  Assuming you mount it to /media/ubuntu, post the outputs of these commands.

```
sudo cat /media/ubuntu/boot/grub/menu.lst (You don't have to include those lines that start with #...)
ls -la /media/ubuntu/boot
cat /media/ubuntu/etc/fstab
```

---

### Post by JohnParker on 2008-11-04
I don't understand, what do I fill into the commands?


cat: /media/ubuntu/disk/boot/grub/menu.lst: No such file or directory

I tried about 60 other ways of doing that, I have the menu.lst file on a usb drive, can I do anything with that?

---

