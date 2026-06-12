---
title: "Grub: Multiple OSes, will only detect bootable Linux partition and Windows"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by altonbr on 2009-06-19
I usually only have one version of Linux and Windows (which, I don't even know why I have really...) but I decided to try bug reporting for Karmic and decided to try Debian stable (5.0.1 Lenny).

I installed Jaunty, then Karmic, then rescued GRUB to boot to Jaunty (Karmic was not found), then installed Debian and rescued GRUB again (I'm in fact still in the LiveCD after doing so), but have found that Grub, again, has not detected my other OSes (besides Windows)...

'update-grub' doesn't seem to help detect the other OSes, so maybe there's a trick I don't know in 'grub'?

Here's what I did to recover my bootloader:
```
grub> find /boot/grub/stage1
 (hd0,1)
 (hd0,6)

grub> root (hd0,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```Here's my fdisk:
```
$ sudo fdisk -l /dev/sda

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x998dde60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5222    41945683+   7  HPFS/NTFS
/dev/sda2   *        5223        6527    10482412+  83  Linux # this is Ubuntu/Jaunty
/dev/sda3            6528       30394   191711677+   5  Extended
/dev/sda5           30264       30394     1052257+  82  Linux swap / Solaris
/dev/sda6            6528        7743     9767457   83  Linux # this is Ubuntu/Karmic
/dev/sda7            7744        8959     9767488+  83  Linux # this is Debian/Lenny

Partition table entries are not in disk order
```OSProber:
```
$ sudo os-prober
/dev/sda1:Windows Vista (loader):Windows:chain
/dev/sda2:Ubuntu 9.04 (9.04):Ubuntu:linux
/dev/sda6:Ubuntu karmic (development branch) (9.10):Ubuntu1:linux
/dev/sda7:Debian GNU/Linux (5.0.1):Debian:linux
```

Relevant GRUB settings:
```
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        cafe5572-7492-4d80-a0f8-62349c42049e
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=cafe5572-7492-4d80-a0f8-62349c42049e ro splash vga=775 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        cafe5572-7492-4d80-a0f8-62349c42049e
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=cafe5572-7492-4d80-a0f8-62349c42049e ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        cafe5572-7492-4d80-a0f8-62349c42049e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=cafe5572-7492-4d80-a0f8-62349c42049e ro splash vga=775 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        cafe5572-7492-4d80-a0f8-62349c42049e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=cafe5572-7492-4d80-a0f8-62349c42049e ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        cafe5572-7492-4d80-a0f8-62349c42049e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```

I know I can edit Grub myself, but I play around with a lot of OSes and would like to know if there is any easier way.

---

### Post by markbuntu on 2009-06-19
Not really. I have 6 OSs scattered across 4 drives on my machine right now and the way I keep everything going smoothly is as follows

Install each system and install its grub/bootloader in the partition with the system. Have one grub on the MBR of the first drive and then just chainload the other grubs from that. If you do this you will not need to rescue grub every time you install a new OS.

It is easy and it saves a lot of headaches you can get with kernel updates etc that will try to overwrite grub if you let them. Many of these kernel updates will assume that the grub they are writing to is on hd(0,0) and will edit the menu.lst assuming hd(0,0) which is a not too unreasonable assumption since they are trying to make it easy for the average user, which you are not.

Instead, refuse the package managers version and just edit the appropriate grub/menu.lst and copy the lines from the last kernel and change the kernel version to the new one.

Once again, this will save you a lot of trouble and it is well worth a few minutes in menu.lst as opposed to a half hour or a few days with a live cd and 5 or 6 Operating systems you cannot use.

Believe me, this is the best way that I have found through much trial and many errors to manage multiple OSs and chainloading is very simple and easy. 

This is the chainload part of the menu.lst that I made myself from the grub on hd(0,0). I only have to change it when I add a new OS to a new drive/partition.

```

#This entry added for 8.04 UnbutuStudio amd64 on sdb

title		Chainload Ubuntu 8.04 amd64
root		(hd1)
chainloader	+1

#This entry added for Debian5 (Lenny) amd64 on sdc

title		Chainload Debian
root            (hd2,0)
chainloader     +1

#This entry added for Mandriva 2009.1KDE
title		Chainload Mandriva
root		(hd2,6)
chainloader	+1

#This entry added for SUSE11.1 on sdd1

title		Chainload SUSE11.1
root		(hd3,0)
chainloader	+1

#This entry added for Jaunty on sdd3
title		Chainload Ubuntu Jaunty 9.04 kernel 2.6.29
root		(hd3,2)
chainloader      +1

```

---

### Post by presence1960 on 2009-06-19
+1 for markbuntu's suggestion. Also when each OS upgrades a kernel you won't have to edit menu.lst of the GRUB on MBR since you're chainloading. Example- if markbuntus  Suse 11.1 upgrades to a new kernel he doesn't have to edit the GRUB in MBR. He chooses the chainloaded entry for SUSE which puts Suse's menu.lst in control, which was auto updated with the kernel. Doing it the other way you will have to manually edit the menu.lst of the GRUB on MBR each time a kernel upgrades (except for the OS in control of that menu).

---

### Post by altonbr on 2009-06-19
Hey, that's fantastic, thanks for the advice! Really helpful.

Now what about adding Grub to each of the OSes without wiping the machine? How would I do that?

I'll then go and edit Grub in the MBR. Sorry, I'm not new to Linux, but I've never really played with Grub.

EDIT: Just out of curiosity, how do you mount your /home partition? Do you load it as /home within every OS and deal with setting conflicts or do you mount your data as, say, /home/brett/data and just load your files from there?

> **presence1960 said:**
> +1 for markbuntu's suggestion. Also when each OS upgrades a kernel you won't have to edit menu.lst of the GRUB on MBR since you're chainloading. Example- if markbuntus  Suse 11.1 upgrades to a new kernel he doesn't have to edit the GRUB in MBR. He chooses the chainloaded entry for SUSE which puts Suse's menu.lst in control, which was auto updated with the kernel. Doing it the other way you will have to manually edit the menu.lst of the GRUB on MBR each time a kernel upgrades (except for the OS in control of that menu).

That makes perfect sense, thanks! Does Grub2 have any better support for multiple OSes?

---

### Post by markbuntu on 2009-06-19
You can install grub on the existing partitions without too much pain, it is pretty easy actually. Open a terminal and type grub, then install grub hd(x,x) or something like that. There is a really good tutorial around here somewhere, just use the forum search for grub install. That's what I do because I can never remember exactly how to do it.

I keep a separate /personal partition with my personal stuff and mount it in my /home/user directory. That way I do not have to worry about all the hidden config files and still have my stuff available. If you use different user names and passwords be prepared for some extensive System/Adminstration/Users and Groups activity.


Grub2 is having serious issues and is pretty borked as far as finding other OSs right now, I would not reccomend going there. If you want to keep up with what is going on with grub2 there is a good thread in the Development and Testing/Karmic Koala forum.

---

