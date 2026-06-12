---
title: "Problems converting Wubi install to dedicated partitions"
date: 2008-09-28
forum: General Help
---

### Post by Zambini on 2008-09-28
Hi, I recently put Ubuntu 8.04 on my laptop via Wubi, and I've been working with it for the past 3 weeks.

I was tired of Windows automatically booting if I turned on my pc and didn't watch it to choose Ubuntu, so I decided to follow the [LVPM walkthrough]("http://ubuntuforums.org/showthread.php?t=438591"), since it seemed to work great. And it did, but I had a lot of things on my grub, including the original Ubuntu (from Wubi), so I tried to uninstall it through Windows (as it says in the LVPM walkthrough), but it couldn't locate the uninstall script.

I had installed Ubuntu via Wubi on a separate partition of my Windows drive, U:/

So I figured I could just format and delete the U:/ partition. ***WRONG***.

Now I can't get into Ubuntu with my laptop. Right now I'm posting this from an old Ubuntu 7.10 LiveCD I have in my "just in case" box I always have available. 

I've been trying to fix it for the past 3 hours, and I haven't been able to fix it. I tried using [SuperGrub ]("http://supergrub.forjamari.linex.org/"), but that didn't work either. 

When I boot up, I see (in grub)
```
Ubuntu 8.04
Ubuntu 8.04 (Recovery Mode)
[Other Operating Systems]
Microsoft Windows XP Professional
[Other Operating Systems]
Windows
Microsoft Windows XP Professional
```

So when I try to choose any of the Ubuntu OS's, I get:
```
Error 17: Cannot mount selected partition
Press any key to continue...
```

Here is my sudo fdisk -l
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbac32136

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7051    56637126    7  HPFS/NTFS
/dev/sda2            8871       10785    15382237+  83  Linux
/dev/sda3           10786       11168     3076447+  82  Linux swap / Solaris

Disk /dev/sdc: 519 MB, 519569408 bytes
129 heads, 32 sectors/track, 245 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         246      507376    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(249, 128, 32) logical=(245, 106, 32)

```
/dev/sda1/ is my Windows partition
/dev/sda2/ is the partition that I copied my old Ubuntu onto via the LVPM walkthrough.
/dev/sda3/ is the swap I made 

I looked at the boot options for Ubuntu 8.04 in the Grub I have, and here is what it says:
```
root (/ubuntu/disk)
kernel /boot/vmlinuz-2.6.24-19-generic root=*....{illegible in the photo I took}*
initrd /boot/initrd.img-2.6.24-19-generic
```

So in summary, just to make your you guys know what I did wrong:
-installed Ubuntu via Wubi on a separate Windows Partition (U:/)
-Converted Wubi install to dedicated partition
-FORMATTED and deleted the Windows Partition (U:/)
-now Ubuntu won't boot 
-have tried SuperGrub, didn't work
-have tried [installing Grub via Live CD]("http://ubuntuforums.org/showthread.php?t=224351"), but didn't work


If you need anything else from me, let me know. I *REALLY* don't want to format my hard drive, because of the large amount of work I've put into making this Ubuntu my own personal comfort OS, but I have to start using this laptop for school this week.

Thanks for any help in restoring my laptop to its functional self!

---

### Post by ago on 2008-09-29
Well I assume you moved wubi to sda2. you can mount that and check the dir content. The grub entry should be

root (hd0,1)
kernel /boot/vmlinuz.... root=/dev/sda2 quiet splash ro
initrd /boot/initrd...

---

### Post by Zambini on 2008-09-29
Thanks for the reply, but I caved in and decided to reinstall. I copied my home directory though, so I can pick through my settings n junk.

---

