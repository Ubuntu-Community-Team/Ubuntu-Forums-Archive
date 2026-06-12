---
title: "Partitioned drive won't boot."
date: 2008-07-28
forum: General Help
---

### Post by ag93ds on 2008-07-28
Hey all, I just installed 8.04 on my Lenovo machine. It has a single hard drive partitioned with 30gb on C: for the OS and ~400gb on D: for storage. I used Vista's partitioner and set aside space on the D drive for Ubuntu and installed it there. 

My problem is when I boot the PC, it automatically boots Windows and does not go into GRUB. In the BIOS my only options are the optical drive, USB, floppy and the hard drive but I can't select which partition to search first. Is there are way to make it default to D to load GRUB? Thanks.

---

### Post by pmdkh on 2008-07-29
Did you choose to install GRUB on the MBR (Master Boot Record) when you installed Ubuntu?

If you didn't do this then Vista's bootloader will still be on the MBR.  Vista's bootloader will then tell the computer to boot to the Vista partition.

I don't think that there is a setting in the BIOS that will tell the computer to boot to a certain partition.  If there was, there wouldn't be much of a need for bootloaders.  (That's just what I understand, I could be wrong.)

---

### Post by ag93ds on 2008-07-29
I didn't see any option when I installed Ubuntu. Is there a way to do it now?

---

### Post by caljohnsmith on 2008-07-30
I'm going mostly from memory, but here is how you would install Grub: if you boot the Live CD, open a terminal, type:
```
sudo fdisk -l
```
To see your drive and partitions. Figure out which is your Ubuntu partition, and then mount it. Say for instance your Ubuntu partition is /dev/sda2:
```
sudo mount /dev/sda2 /mnt
```
Then to install Grub to the MBR, and have it point to the Ubuntu partition for its configuration files, use the following command:
```
sudo grub-install --root-directory=/mnt /dev/sda
```
And replace "sda" with whatever is your HDD from the first step (if it is different). The main point is don't give that grub-install command above a partition, e.g. sda2, because that will install Grub to the boot sector of that particular partition, not the MBR. 

That should install Grub to the MBR, but I think you will still have to create a menu.lst (the file that determines the selections you are given in Grub's startup menu). To do that:
```
sudo chroot /mnt
update-grub
```
That should create a /boot/grub/menu.lst file in your Ubuntu partition. Hopefully Grub will make a menu.lst that will "just work" with your Windows/Ubuntu partitions, but if you have any problems we can give help modifying your menu.lst.

---

### Post by ag93ds on 2008-07-30
Thanks, I'll try this out when I get back in town and let you know how it went.

---

### Post by sstvinc2 on 2008-07-30
Also, you could look into Super Grub Disk ([http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")).  You can burn the iso to a CD that you can boot.  It's got a pretty simple interface that should let you install grub on your C: drive's MBR.

I had kind of a similar problem, where my BIOS tried to boot the wrong disk (the disk it tried to boot only had data, no OS, on it).  There might be an option in your BIOS like there is in mine to set the hard disk boot priority, which just decides which HDD to slot into your overall boot priority.

---

