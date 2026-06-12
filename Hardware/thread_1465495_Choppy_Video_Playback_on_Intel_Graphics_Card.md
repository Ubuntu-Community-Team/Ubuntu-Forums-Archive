---
title: "Choppy Video Playback on Intel Graphics Card"
date: 2010-04-29
forum: Hardware
---

### Post by taoist_jeff on 2010-04-29
Howdy All,

Long time reader first time poster.  Hopefully this won't turn into a "plz halp m3" post, but we'll see where it goes.  The wife's laptop, a Toshiba, just recently went out.  It ran Karmic Koala pretty well, and we used it as a nice little machine to curl up in bed and watch movies.  So, she pops over to the local Fry's and picks up this guy, an Acer Aspire 77400-6656.  We swapped the hard drive disks and every thing appears to be working fine, better even.  The only issue we're having is that video playback (in either VLC or Movie Player) is rather choppy.

Here's an lspci paste:

00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Arrandale Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

We're currently running the latest version of the xserver-xorg-video-intel, which if I have read correctly is based on the xf86-video-intel driver posted at Intel's linux site.  I've tried downgrading the driver to no avail.

Is this just a case of waiting for the next version of the driver to be released, or are there some other areas I should at to increase playback quality?  Should any other information be helpful in trying to improve this situation, ask and you shall receive :).

---

### Post by gordintoronto on 2010-04-29
I think that is the video support built-in to Intel's I3 processor? I have read elsewhere that the proper driver is still months away.

---

### Post by taoist_jeff on 2010-05-01
This is pretty much what I thought.  I wrongly assumed that the current Synaptic package was using the latest driver released on Intel's site, but apparently I was wrong.  The wife actually downloaded, compiled, and installed the most recent version from the site (apparently I married well), I think it was version 2.11.0?  Any way, there was a moderate performance increase, nothing worth while.  I suppose this is just one more example of making sure to double and triple check the hardware compatibility pages before buying some new equipment :|.

---

