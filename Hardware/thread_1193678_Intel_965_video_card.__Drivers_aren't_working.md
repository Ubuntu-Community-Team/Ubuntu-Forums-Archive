---
title: "Intel 965 video card.  Drivers aren't working?"
date: 2009-06-21
forum: Hardware
---

### Post by xxxxme on 2009-06-21
I have Ubuntu 9.04 installed on this Dell Inspiron 1525 (generic hardware for such) with the gnome desktop.  Every program was updated to the latest version update-manager showed as of a day or two ago.
   I can use the desktop, xine, the gimp, firefox, and other things fine, but when I try using blender, and certain games under wine, I have problems.
[http://img5.imageshack.us/img5/8609/screenshotpiu.png](http://img5.imageshack.us/i/screenshotpiu.png/)
Is what I see in blender.  Since it isn't obvious, I should say that the lighter section underneath the default cube will keep images of things dragged over it, as it is doing with the axis on its bottom left.

lspci reports an Intel 960 or 965 sort of video card:
```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```

Is this a driver problem, as suggested on #ubuntu, or is it something else?  Either way, what can I do about it?

---

### Post by Artisten on 2009-06-25
I have the same card and are experiencing the same problems.

Any suggestions? Did you find a sulution?

Thanks.

EDIT: Found the bug at launchpad:
----
but it's not solved there.

EDIT2:
Found more bug reports:
[Bug #353763]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/353763")
[Bug #364030]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/364030")
[Bug #365776]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/365776")
[Bug #360415]("https://bugs.launchpad.net/ubuntu/+source/blender/+bug/360415")

---

### Post by Artisten on 2009-06-25
After reading the bug discussions, it seems like there are a bug in the Intel driver.

The only workaround that works for me so far is running this:
```
LIBGL_ALWAYS_SOFTWARE=1 blender
```

But the viewport is very slow, and I can't use Blender like this on a long-term.

---

### Post by xxxxme on 2009-06-27
I have not been able to find a solution yet.
Hmm, starting blender with that option works for me, too, but I don't immediately see that it's slow (I only have a couple simple models on this computer, though.)

---

### Post by suso on 2009-07-30
> **Artisten said:**
> After reading the bug discussions, it seems like there are a bug in the Intel driver.

The only workaround that works for me so far is running this:
```
LIBGL_ALWAYS_SOFTWARE=1 blender
```

But the viewport is very slow, and I can't use Blender like this on a long-term.

Thank you very much for posting this workaround.  I didn't know you could do that and now I can at least USE blender on the laptops I have with an Intel card.

What is weird is that I just upgraded one of my laptops from 8.04 to 9.04 today and before Blender was working fine in GL mode, now its having this problem.  So something in the driver changed, but I think I've had this problem since before 8.04 even.

---

