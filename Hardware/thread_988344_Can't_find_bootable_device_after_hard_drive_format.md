---
title: "Can't find bootable device after hard drive format"
date: 2008-11-20
forum: Hardware
---

### Post by rschnitzel721 on 2008-11-20
Ok so here is the skinny on what I did.
   I used gdeparted on the Ubuntu live Cd to erase my windows partition as I have found the joys of vmware workstation.  The deleting and resizing of my hard disk went fine.  But when I went to reboot my computer couldn't find a bootable device.
   So far I have only reconfigured my grub menu.  But my bios shows my hard drive, I can access my hard drive in Ubuntu live Cd, and I can boot the Ubuntu that is installed on my hard drive if I start the live Cd and then choose boot from first hard disk in the initial options screen.  I am running Hardy Heron and just let me know what other diagnostics you need and the command to get them.
   Thanks for all your help!!!

---

### Post by cariboo on 2008-11-20
You probably wiped the master boot record when you reformated the hard drive, you have to reinstall grub to repair this problem. To do this once you have booted to the desktop, open a Applications-->Accessories-->Termianl and type:

```
sudo grub-install
```

enter your password and follow the prompts.

Jim

---

### Post by caljohnsmith on 2008-11-20
> couldn't find a bootable device
That type of BIOS error can happen if you don't have one of your partitions marked as bootable on the drive, because some BIOSes will refuse to boot a drive without a boot flag set on one partition; basically, the BIOS assumes the drive is a data drive if a boot flag isn't set. That's probably your case, because most likely your Windows partition had the boot flag set; and you said you deleted it. 

You can check with:
```
sudo fdisk -l
```
And if there is no asterisk (*) next to any of the partitions under the "boot" heading, then you can set the boot flag on a partition by doing:
```
sudo fdisk /dev/sda
```
Press "a", enter the partition number (should be a primary partition or an extended partition, but not a logical one), "w" to write the change, and finally "q" to quit. 

If that works to boot the drive, but you then get a Grub error, let me know and I can help you fix that too if you want. :)

---

