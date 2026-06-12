---
title: "RAM Upgrade"
date: 2011-05-04
forum: Hardware
---

### Post by King_Koopa on 2011-05-04
I just got a second stick of memory to install in my Ubuntu laptop and I'd like to know if I have to do anything within in Ubuntu for the OS to see and use the extra RAM.

I have done plenty of RAM upgrades in Windows and am familiar with updtaing the page file in that environment, but this will be my first Ubuntu memory upgrade.

Thanks for any help in advance. :-)

---

### Post by plucky on 2011-05-04
> **King_Koopa said:**
> I just got a second stick of memory to install in my Ubuntu laptop and I'd like to know if I have to do anything within in Ubuntu for the OS to see and use the extra RAM.

I have done plenty of RAM upgrades in Windows and am familiar with updtaing the page file in that environment, but this will be my first Ubuntu memory upgrade.

Thanks for any help in advance. :-)

If the BIOS can see the memory,then the operating system will use it.

If you want to hibernate,you will have to increase the size of the swap partition to at least the size of memory.Increasing the size of swap will change the UUID of the partition,so it will have to be changed in the /etc/fstab file. and the /etc/initramfs-tools/conf.d/resume file.

Good Luck

---

### Post by King_Koopa on 2011-05-04
> **plucky said:**
> Increasing the size of swap will change the UUID of the partition,so it will have to be changed in the /etc/fstab file. and the /etc/initramfs-tools/conf.d/resume file.

Good Luck

Thanks for the help.

I know I can find the UUID by using:

```
ls /dev/disk/by-uuid
```

Would these commands work ok for changing the UUID within Ubuntu?

```
gksudo gedit /etc/fstab
```

```
gksudo gedit /etc/initramfs-tools/conf.d/resume 
```

---

### Post by plucky on 2011-05-04
> I know I can find the UUID by using:

ls /dev/disk/by-uuid


Try ```
sudo blkid
``` gives a better format.

> Would these commands work ok for changing the UUID within Ubuntu?

gksudo gedit /etc/fstab

gksudo gedit /etc/initramfs-tools/conf.d/resume


Yes

Good Luck

---

