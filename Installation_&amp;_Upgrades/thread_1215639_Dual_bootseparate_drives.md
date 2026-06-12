---
title: "Dual boot/separate drives"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by Stan57 on 2009-07-17
I have finally been able to install ubuntu to a separate drive. I have Vista 64 bit premium installed on one drive C-drive and this thing installed on its own drive D-Drive. Now it wont boot to ubuntu what soever. it goes to a grub prompt and is waiting instruction,like i know what to do??
What can i do to fix this pleaseeeeeeeeeeeeee

---

### Post by merlinus on 2009-07-17
Did you do a wubi install, in other words, inside of windows, or install ubuntu separately?

---

### Post by Stan57 on 2009-07-17
> **merlinus said:**
> Did you do a wubi install, in other words, inside of windows, or install ubuntu separately?

Installed separate not a windows install

---

### Post by merlinus on 2009-07-17
Can you boot from the live cd?  If so, open a terminal and post results of

```
sudo fdisk -l
```

Also, what is the hdd boot order in bios?

And fwiw, linux, unlike windows, does not use drive letters.  It uses partitions, e.g. sda1, which would translate to first hdd, first partition.

---

### Post by Stan57 on 2009-07-17
> **merlinus said:**
> Can you boot from the live cd?  If so, open a terminal and post results of

```
sudo fdisk -l
```

Also, what is the hdd boot order in bios?

And fwiw, linux, unlike windows, does not use drive letters.  It uses partitions, e.g. sda1, which would translate to first hdd, first partition.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d9d86a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59349   476720811   83  Linux
/dev/sda2           59350       60801    11663190    5  Extended
/dev/sda5           59350       60801    11663158+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bea9bea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09cee67e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        7872     2015216    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ 


didnt check the boot order though

---

### Post by merlinus on 2009-07-17
ubuntu is on sda1 (first hdd, first partition), and vista on sdb1 (second hdd, first partition), but the booting order of your hdds is vital.  Check and post back.

---

### Post by Stan57 on 2009-07-17
> **merlinus said:**
> ubuntu is on sda1 (first hdd, first partition), and vista on sdb1 (second hdd, first partition), but the booting order of your hdds is vital.  Check and post back.

The drive that has ubuntu on it boots second or third if want to be techinal
1. Ch6 M St3500    Vista drive
2.USb
3.CH1 M Ubuntu HDD

---

### Post by merlinus on 2009-07-17
Try changing the order so the linux hdd is first, and see what happens.

---

### Post by Stan57 on 2009-07-17
> **merlinus said:**
> Try changing the order so the linux hdd is first, and see what happens.

It said no operating system

trying to boot to linux gets me 

Grub> _

---

### Post by merlinus on 2009-07-17
If it said no operating system, then how did you get to the grub prompt?

Another thing to try is booting from the live cd and mounting your linux hdd via nautilus.  Then navigate to /boot/grub/menu.lst, and post its contents.

---

### Post by Stan57 on 2009-07-17
> **merlinus said:**
> If it said no operating system, then how did you get to the grub prompt?

I switched it back off course,i get to the screen where i have a choose of Windows or linux to boot from. if i choose linux it goes as far as that grub prompt. i have windows on one drive and Ubuntu on the other drive

---

### Post by merlinus on 2009-07-17
Yes, I understand that each os is on a separate hdd.  Try running from the live cd, mount your linux drive, and post contents of /boot/grub/menu.lst.  That is where grub keeps its booting info.

Also, will grub boot vista?

---

### Post by Stan57 on 2009-07-17
> **merlinus said:**
> Yes, I understand that each os is on a separate hdd.  Try running from the live cd, mount your linux drive, and post contents of /boot/grub/menu.lst.  That is where grub keeps its booting info.

Also, will grub boot vista?

I have no problem booting to Windows,and how do i mount my linux drive? i have no clue how to do that,booing from the cd is no problem

---

### Post by merlinus on 2009-07-17
So grub will boot to windows, but not ubuntu?  Just checking....

You can run nautilus from Places whilst using the live cd, and see if your ubuntu partition is listed.  If not, we can manually mount it via terminal commands, and be able to look at menu.lst.

My best guess at this point is that grub was not installed correctly.

---

### Post by Stan57 on 2009-07-17
> **merlinus said:**
> So grub will boot to windows, but not ubuntu?  Just checking....

You can run nautilus from Places whilst using the live cd, and see if your ubuntu partition is listed.  If not, we can manually mount it via terminal commands, and be able to look at menu.lst.

My best guess at this point is that grub was not installed correctly.

I have no clue how to do that,i need step by step directions please.

---

### Post by pd71sat on 2009-07-17
> **Stan57 said:**
> I have no problem booting to Windows,and how do i mount my linux drive? i have no clue how to do that,booing from the cd is no problem

Try the following to mount your Linux hard drive after you boot 
up from the live cd:
First ensure that you are in your native directory (does not 
have to be, just a known point that you should have access to);

**cd ~/**
**mkdir boot_disk**
**sudo mount /dev/sda1 ~/boot_disk**

That last command should now let you view the contents of the
"boot_disk" folder as the starting root tree of the "/dev/sda1"
that the "sudo fdisk -l" command showed as belonging to Linux.

There should be a file "~/boot_disk/boot/grub/menu.lst" that you
you can get the contents and post for **merlinus** to see.

good luck.

---

### Post by konnorrigby on 2009-07-17
i suggest re-installing ubuntu and and making sure it's on the right hdd. and making sure grub is also on that one through advanced at the end of the installation.

---

### Post by Stan57 on 2009-07-18
> **konnorrigby said:**
> i suggest re-installing ubuntu and and making sure it's on the right hdd. and making sure grub is also on that one through advanced at the end of the installation.

Ive gave up,i installed opensuse11 and it boots just fine but the graphics is only allowing 800X600 on a 1400x900 desktop. going to wipe that also,just too many problems. Thanks for all your help though

Stan

---

