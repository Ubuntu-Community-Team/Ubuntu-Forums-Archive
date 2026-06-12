---
title: "HDD mounting issue"
date: 2021-07-18
forum: Hardware
---

### Post by cassuciminer on 2021-07-18
[FONT=Whitney]Hi all. I ran into a problem adding a HDD in Linux I can't seem to get fixed. Hope someone can give me a hand.I'm new to Ubuntu and its commands so bear with me. Got loads of windows experience though. So i'm learning quick.My System has 6 SATA ports and 2 x M.2 sockets. Got 2 NVME's in the M.2 Sockets. A SSD for the operating system. And 3 x 18 TB HDD . A.s of yesterday I wanted to ad another 18 TB to the system but it was not showing up in the bios. As i shoot have known my Asus B550 F shuts down SATA port 5 & 6 if the M.2 sockets are used.A.s I can manage with only one NVME. Got the second one out and plugged the 18 TB HDD in port 5. All good. HDD showed up in the Bios.After formatting the HDD and mounting it something strange happens. No errors came up during formatting, mkdir and mounting commands.Al my disks are mouted in : HDD1 at /mnt/HDD1, HDD2 at /mnt/HDD2, HDD3 at /mnt/HDD3But if I use command : sudo mount dev/sde /mnt/HDD4    it is mount at /mnt/HDD41.I can see the drive in disks but I can't acces it. I tried to find a solution researching it in google. Spend a hours now but nothing seems to work. I can only find mounting solutions for networking issues.Thanks[/FONT]

---

### Post by ajgreeny on 2021-07-18
Welcome to the forum.

We need to know more about the disk that is giving you this problem so please run the two following commands in terminal and copy back here the output you see.
```
sudo fdisk -l
sudo lsblk -O
```
The easy way to copy from terminal is to highlight the text you want, right click and choose Copy from the context menu.

That should show us all disks attached to the computer and the partitions on the disks and how they are formatted, ie which filesystem.
If it is formatted to a Linux filesystem, which is what it really should be, you may simply need to change ownership or the partitions' permissions, but let's see what the output is first.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by TheFu on 2021-07-18
```
sudo mount dev/sde /mnt/HDD4
```
shouldn't work.

```
sudo mount /dev/sde1 /mnt/HDD4
```

I suspect your Windows background has warped your views of what a disk is and what a partition is.  I hope you created a partition table on the disks before doing anything else.  While Linux will let us do what we want, even when it is a bad idea, the best practice for all storage is to have a GPT partition table on all storage.

Then you'd want to create 1 or more partitions. Normally, this would depend on the size of your backup disk capacity, so if you backup disks are 4TB, then you'd never want to make any partition larger than 4TB.  Of course, if you use the advanced enterprise storage volume management provided by ZFS or LVM2 or BTRFS, then there are other possible techniques.

Next, we need to know what file system was put onto the partition (or into the Logical Volume, if you are using LVM).  There are 50-ish different file systems that Linux supports.  Which you used determine the next questions and next steps to provide access.

Always remember, Linux is a multi-user OS and that goes to the connected storage as well. Even if there is only 1 human accessing the system, the OS is still using 10 - 100 different userids. Generally, making storage writable by all users is terrible security and should be avoided. Just because MSFT does something, that doesn't make it a good idea. Always remember that.

**df -Th** is helpful for all currently mounted storage in addition to the commands already requested.

Lastly, reading walls-of-text is hard.

---

