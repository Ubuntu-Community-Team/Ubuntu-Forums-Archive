---
title: "Gigabyte 990FX / VIA V63608 boot issues Xubuntu 15.04"
date: 2015-08-24
forum: Hardware
---

### Post by cfmackey on 2015-08-24
Hi there everyone,

My rig has a Gigabyte GA-990FXA-UD3 (rev. 4.0) motherboard, which features a VIA VT6308 USB 3.0 controller.
Originally this board was problematic in that the ethernet, PCI Wi-Fi card and USB 3.0 ports did not work at all. I was able to solve this by adjusting the EHCI and XHCI hand-off, Legacy USB and IOMMU settings in the UEFI. Presently the USB, wifi and ethernet all work, but at a price.
The trade-off being that now my machine takes a reeeally long time to boot, if it boots at all. My dual-booted Windows installation, however takes no more than 10 seconds to boot.
I decided to have a look at dmesg, and here's the notable output:

```
  
[    1.131837] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.131843] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 1
[    1.131873] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0017 address=0x00000000be9f9880 flags=0x0010]

```

That last message "AMD-VI:..." repeats an incredible amount of times, until the system appears to give up:

```

[   17.990088] xhci_hcd 0000:02:00.0: can't setup: -110
[   17.990158] xhci_hcd 0000:02:00.0: USB bus 1 deregistered
[   17.990205] xhci_hcd 0000:02:00.0: init 0000:02:00.0 fail, -110
[   17.990251] xhci_hcd: probe of 0000:02:00.0 failed with error -110

```

At which time, the system picks up where it left off, and boots normally. 
Obviously there's an issue with device "02:00.0", so I decided to have a look at that too. Here's the pertinent output from lspci:

```

02:00.0 USB controller: VIA Technologies, Inc. Device 3483 (rev 01)

```

Which makes sense. I didn't have this issue before I fixed the USB, wifi and ethernet issues with the UEFI settings. It looks like the system can't communicate with the USB controller.
So I went back into the UEFI and messed around with those settings again, but no dice. It seems I can either have working USB, Wifi and Ethernet, *or* a fast boot time...not both.
I poked around the forums a bit, but nobody seems to be having the same issue I do. I also tried to search for a driver for that VIA VT6308 chipset, but there's nothing available for Linux.
I'll continue to poke around with settings and various boot options, but I think I'm missing something here.

Any help is greatly appreciated, thanks for reading through!

---

### Post by oldfred on 2015-08-24
I think these mostly discuss the IOMMU issue. But perhaps some more info?

 Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by cfmackey on 2015-08-25
Perfect! The second link you gave seemed to make a huge improvement.

From this post: [http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
> [COLOR=#000000]Disabling IOMMU in my BIOS and then adding [/COLOR][COLOR=#008000]*GRUB_CMDLINE_LINUX="iommu=soft" *[/COLOR][COLOR=#000000]to grub reduced my boot time from 57 seconds to 11 seconds. Thank you! [/COLOR]

So following that suggestion, I added the following line to my grub config:
```
GRUB_CMDLINE_LINUX="iommu=soft"
```

Now I no longer see the "AMD-Vi" page fault messages in dmesg, and my boot time is significantly better.
It however didn't seem to make a difference whether I enabled or disabled IOMMU Controller in the UEFI. But I'll investigate that a bit more.

For now the problem seems to be solved, so I'm going to mark the thread accordingly. Thanks for the help!

---

