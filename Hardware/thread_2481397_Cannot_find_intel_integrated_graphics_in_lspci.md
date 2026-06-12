---
title: "Cannot find intel integrated graphics in lspci"
date: 2022-11-28
forum: Hardware
---

### Post by Peter_Brandon on 2022-11-28
I'm trying to configure my computer so the monitor is handled by intel integrated graphics, leaving my GPU free to do some light computation work (it's an old system).  According to Intel's website, my chip has integrated graphics, albeit with an asterisk that this may not be available on some systems (but I imagine that has to do not with the chip's capabilities but what ports are made available on the tower).  My tower has two DVI ports coming off the motherboard (hence intel).  These are covered over, but the system was meant to use a GPU, so I suspect that the covers are just to prevent the user from plugging into the 'wrong' graphics.

So, I think I should have intel graphics, but lspci only shows a graphics capability for the GPU:


```
$ sudo lspci
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 745] (rev a2)
01:00.1 Audio device: NVIDIA Corporation GM107 High Definition Audio Controller [GeForce 940MX] (rev a1)
```


I have firmware-misc-nonfree and xserver-xorg-video-intel and mesa-utils (plus a load of files that come with that) installed.  If I can't find the pci address for the intel vga, then I can't set up xorg.conf to have that as my screen0.  Anyone have any idea why my integrated graphics aren't showing?  I suppose there's some chance they are disabled somehow.

---

### Post by aljames2 on 2022-11-28
All I can offer is to check in your bios to see if your onboard graphics is enabled.

---

### Post by Peter_Brandon on 2022-11-30
> **aljames2 said:**
> All I can offer is to check in your bios to see if your onboard graphics is enabled.

Thanks          aljames2, that was spot on!  I didn't realize that the BIOS might be used to turn of integrated graphics.  I've turned it on and seen it on a screen, though the OS is a bit confused about which card to use--but I can work with that.

---

