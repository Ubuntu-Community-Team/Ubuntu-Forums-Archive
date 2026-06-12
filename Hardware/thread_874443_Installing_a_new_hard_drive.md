---
title: "Installing a new hard drive"
date: 2008-07-29
forum: Hardware
---

### Post by DarchAengel on 2008-07-29
I'm looking to buy a new hard drive for my linux box.  I have done many things...upgrading my hard drive is not one of them.  I know with my Mac, my friend had to "bless" or something or other before I could change my hard drives otherwise the OS would not have transferred properly.  Is this something I need to worry about with Ubuntu?  Is is just as simple as slaving the drive and copying or do I need to buy more hardware/download some special software?

---

### Post by warp99 on 2008-07-30
> **DarchAengel said:**
> I'm looking to buy a new hard drive for my linux box.  I have done many things...upgrading my hard drive is not one of them.  I know with my Mac, my friend had to "bless" or something or other before I could change my hard drives otherwise the OS would not have transferred properly.  Is this something I need to worry about with Ubuntu?  Is is just as simple as slaving the drive and copying or do I need to buy more hardware/download some special software?

After you copy the data with the correct permissions you need to install the Grub bootloader to the MBR of the new drive and also change the UUID values in '/boot/grub/menu.lst' and in the file '/etc/fstab' to the new drive. You can get the values with the following command:

```
sudo vol_id -u /dev/xxxx
```

replacing xxxx with the name of your new partition (hda1, hda2, sda1, sda2, etc.). Follow this guide to install Grub to the new drive:

[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

Edit:

I assume that you have already partitioned the new drive and built a file system using mkfs. If not here is a guide that can help you:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by logos34 on 2008-07-30
[InstallingANewHardDrive - Community Ubuntu Documentation]("https://help.ubuntu.com/community/InstallingANewHardDrive")

---

### Post by rmjohnson144 on 2008-08-02
> **logos34 said:**
> [InstallingANewHardDrive - Community Ubuntu Documentation]("https://help.ubuntu.com/community/InstallingANewHardDrive")

Thanks very much!  I've been looking for this for a few days now.

-=Mark

---

