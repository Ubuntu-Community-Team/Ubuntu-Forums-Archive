---
title: "Issues with my sd card reader on Linux 3.16.RCx"
date: 2014-07-24
forum: Hardware
---

### Post by GOESSEL_Guillaume on 2014-07-24
Hello,
I'm the owner of a Lenovo Yoga 2 13 and my Wifi adapter is not well supported on Linux versions prior to 3.15 so I tried (and succeeded) to install the latest available test version of the Linux kernel (3.16.rc6 at this time) downloaded from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) .
But I was supprised that my internal SD Card reader stopped working (the card is not mounted and nothing shows up at dmesg when I plug it) whereas is was working fine under Linux 3.13.x .
I will try with different kernel versions to see when it broke and I will post the output of lspci related to each version and I will also try with Ubuntu14.10 updated to Linux 3.16.rc6
I hope we will be able to find where this bug come from and if the patch can be upstreamed before 3.16 final release.

Thank you for reading and stay tuned for my results.

PS : I'm posting this here and I didn't open a bug ticket because I'm not 100% sure whether the issues comes from me or not ^^

EDIT : 
Here are my results
It's woking under Ubuntu 14.04 and Linux 3.15.6
It's not working with Linux 3.16.rc5 with both 14.04 and 14.10
The lspci output is always the same : > 00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter

EDIT : I forgot to do lsusb  ...
so my card reader is > Bus 002 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
and to make it work you have to do insert the rtsx_usb module : > sudo modprobe rtsx_usb

---

### Post by GOESSEL_Guillaume on 2014-08-08
I don't really know what to do...
I took two dmesg running 3.15(working) and 3.16(not working) but I don't find anything helpfull

---

### Post by cariboo on 2014-08-09
Moved to the Hardware sub-forum.

---

### Post by Cliff_Simonds on 2014-08-09
I'm using the Ubuntu 14.10 Utopic dev and it has 3.16.0-6 generic and my sd card reader works fine. you could try that kernel. Read [[COLOR=#4b0082]this[/COLOR]]("http://www.yourownlinux.com/2014/08/how-to-install-linux-kernel-3-16-stable-in-linux.html") at Your Own Linux. At the comments section at the bottom someone using Trusty has 3.16 stable installed and claims it's working great. good luck:)

---

### Post by GOESSEL_Guillaume on 2014-08-13
Ok so I have good news
my sd card reader is Bus 002 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
I googled it and it seems that the driver was added to 3.16 kernel ( see [http://lwn.net/Articles/601726/](http://lwn.net/Articles/601726/) )
And if I manually do > modprobe rtsx_usb sd cards are recognized well
So the issue is that the rtsx_usb module isn't automatically added at boot
I should report a bug to launchpad right ?

Thanks for your time

EDIT : I've tested with Utopic fully updated as of 13 August 2014 ( kernle 3.16.0-7 ) and with Trusty with 3.16.0-031600 kernel (the latest on [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) )

---

### Post by GOESSEL_Guillaume on 2014-08-23
For the record a bug was submitted here (not by me) : [https://bugzilla.novell.com/show_bug.cgi?id=890096](https://bugzilla.novell.com/show_bug.cgi?id=890096)
The patch [https://lkml.org/lkml/2014/8/8/896](https://lkml.org/lkml/2014/8/8/896) was merged in 3.17 kernels

Closing this thread as SOLVED

---

