---
title: "[SOLVED]Can't mount nor format floppy drive"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by ubuntu_demon on 2006-08-09
Hi,

I made a new thread for this because everyone has different hardware and I've tried all the solutions I know (although I never use floppy drives)

I'm helping someone with Ubuntu. I can't mount nor format floppies on one of his machines.

If tried adding this to /etc/fstab :
```

/dev/fd0        /media/floppy0  auto    rw,user,noauto 0 0

```

The floppy0 folder does exist.

When I do :
$sudo mount /dev/fd0 /media/floppy0

nothing happens

The motherboard is a chaintech 9EJL1.

```

$lspci

0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 11)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 11)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:03.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
0000:02:03.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
0000:02:03.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

```

I forgot to try hdparm :(. I will do that tomorrow. 

I opened the case and everything looked alright. I might try a different floppy drive and cable tomorrow.

Here's another strange problem I have with the same pc :

grub mapping problem. Can't boot into windows
[http://www.ubuntuforums.org/showthread.php?t=233008](http://www.ubuntuforums.org/showthread.php?t=233008)

We are going to try to flash the bios tomorrow.

Any suggestions ?

Thanks,

ubuntu_demon

---

### Post by wpshooter on 2006-08-09
Do you have all of the available updates for Ubuntu downloaded and installed ?

---

### Post by ubuntu_demon on 2006-08-09
> **wpshooter said:**
> Do you have all of the available updates for Ubuntu downloaded and installed ?
Yes. Thanks for the suggestion though :).

It's running the linux-686 kernel with all upgrades installed. (I will be again over at his house tomorrow)

---

### Post by Cariboo1938 on 2006-08-09
> **ubuntu_demon said:**
>  Here's another strange problem I have with the same pc :
grub mapping problem. Can't boot into windows
[http://www.ubuntuforums.org/showthread.php?t=233008](http://www.ubuntuforums.org/showthread.php?t=233008).....
ubuntu_demonIs your /boot/grub/menu.lst up to date...?I had the same problem and after entering 
[COLOR="DeepSkyBlue"]title           Windows XP
root       (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
ma         (hd1) (hd0)
chainloader +1[/COLOR]
to the menu.lst I could choose between Linux and Windows when booting. The default timeout is set to 3 sec, so you have to be quick when it comes to open the GRUB window. (I'm a bit slow, so I changed the timeout to 30s.)
I hope it helps:)  
Juergen

---

### Post by ubuntu_demon on 2006-08-09
> **Cariboo1938 said:**
> Is your /boot/grub/menu.lst up to date...?I had the same problem and after entering 
[COLOR="DeepSkyBlue"]title           Windows XP
root       (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
ma         (hd1) (hd0)
chainloader +1[/COLOR]
to the menu.lst I could choose between Linux and Windows when booting. The default timeout is set to 3 sec, so you have to be quick when it comes to open the GRUB window. (I'm a bit slow, so I changed the timeout to 30s.)
I hope it helps:)  
Juergen
I'm also experiencing problems with grub (can't boot into windows) with his pc. See :

grub mapping problem. Can't boot into windows
[http://www.ubuntuforums.org/showthread.php?t=233008](http://www.ubuntuforums.org/showthread.php?t=233008)

---

### Post by ubuntu_demon on 2006-08-10
His floppy drive wasn't connected at all.

LOL :-D

SOLVED

---

