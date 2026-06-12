---
title: "Hammerhead RT800"
date: 2011-06-15
forum: Hardware
---

### Post by rmannon on 2011-06-15
Hi all!

So I think I have a stumper for everybody.  It has me going in circles and I hope somebody can really point me in the right direction.

I have picked up a Hammerhead rt800 and an RT933.  They are both rugged little devices that use a pen on the screen and that's where the problem resides.  I am able to load natty on them but the screens do not work.  If I connect them to a monitor I am able to see the desktop but the screens themselves do not work.

I do not know if this helps but here is the output from lspci:

Board:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 03)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 42)


What steps do you guys suggest in troubleshooting this further? I have already tried noacpi and acpi=off in the boot parameter in grub to no avail.  

Thanks for your help!

---

