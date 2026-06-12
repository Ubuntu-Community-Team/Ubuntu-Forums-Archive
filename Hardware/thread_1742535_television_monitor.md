---
title: "television monitor"
date: 2011-04-28
forum: Hardware
---

### Post by newbiefly on 2011-04-28
i use my tv (720p) as a 2nd monitor but since the upgrade to natty can't get the monitor settings right.  i have tried all available resolutions and detecting monitors but none of that seems to work.  Help, please.[IMG]https://picasaweb.google.com/lh/photo/Emm3owPDF6rypVCAo9WCRA?feat=directlink[/IMG]

---

### Post by papibe on 2011-04-29
what is your graphic card?

---

### Post by newbiefly on 2011-04-29
Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller?

```
fly@fly-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
fly@fly-laptop:~$ 

```

---

### Post by newbiefly on 2011-04-29
I've been trying this:
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting](https://wiki.ubuntu.com/X/Config/Resolution#Resetting) an out-of-range resolution

over and over i try to edit xorg.conf but end up ruining the gui and having to run sudo rm /etc/X11/xorg.conf from the command line

i was trying xrandr to no avail and repeated the steps to post here:

```
fly@fly-laptop:~$ cvt 1280 720
# 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHz
Modeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
fly@fly-laptop:~$ xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
fly@fly-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 2304 x 800, maximum 8192 x 8192
LVDS1 connected 1280x800+1024+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
TV1 unknown connection (normal left inverted right x axis y axis)
   848x480        30.0 +
   640x480        30.0 +
   1024x768       30.0  
   800x600        30.0  
  1280x720_60.00 (0xcc)   74.5MHz
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock   44.8KHz
        v: height  720 start  723 end  728 total  748           clock   59.9Hz
fly@fly-laptop:~$ xrandr --addmode VGA1 1280x720_60.00
fly@fly-laptop:~$ xrandr --output VGA1 --mode 1280x720_60.00
fly@fly-laptop:~$ 

```

and after adjusting an overlap in monitor preferences things are right!

HOORAY!

i will never allow upgrade tools to delete xorg.conf ever ever again!

---

### Post by papibe on 2011-04-29
I'm glad you solved it. Keep a copy of your working xorg.conf in your home, so in the worst case (either a bad update, or an app that doesn't tell you that modifies the file), you can be safe.

Regards.

---

### Post by voodoostevie on 2011-04-29
> **papibe said:**
> I'm glad you solved it. Keep a copy of your working xorg.conf in your home, so in the worst case (either a bad update, or an app that doesn't tell you that modifies the file), you can be safe.

Regards.

Tough to save a working xorg.conf if you are not updating the system but coming from a clean install. This has been marked as a bug for xserver-xorg-video-intel ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/763688]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/763688")).

I am wondering if something in the xorg.conf is not being written properly for the external monitors.

---

### Post by newbiefly on 2011-05-03
Thanks for your interest papibe and voodoostevie.  I actually don't have an xorg.conf right now (never could get it right always with the removing and rebooting over and over) 

instead i created ~/.xprofile that looks like this:
```
xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
xrandr --addmode VGA1 1280x720_60.00
xrandr --output VGA1 --mode 1280x720_60.00 --rate 60
xrandr --output LVDS1 --mode 1280x800 --rate 60
xrandr --output VGA1 --left-of LVDS1
```

cause i was having to open terminal and do these commands manually ugh. but now when i restart my settings are as i like.  i hope there aren't too many others experiencing this issue.

---

### Post by newbiefly on 2011-05-03
o hay voodoostevie

here is lspci -v in case it might help with the bug you guys are working on.
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5110 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0
	Memory at 92500000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

```

---

### Post by Frankie9 on 2011-05-15
I am running an old amd turion 64 processor with an ati radeon xpress 200m in my old laptop (compaq presario v2607cl) and I am still experiencing this issue. I was able to get my graphics card to work and use my vga output, but my s-video still doesn't work. 
Is this fix only for intel based computers, or a general fix? If it is a general fix, I don't really know what it means, so is there a step by step process available or an update for x.org?

---

### Post by newbiefly on 2011-09-08
> **Frankie9 said:**
> I am running an old amd turion 64 processor with an ati radeon xpress 200m in my old laptop (compaq presario v2607cl) and I am still experiencing this issue. I was able to get my graphics card to work and use my vga output, but my s-video still doesn't work. 
Is this fix only for intel based computers, or a general fix? If it is a general fix, I don't really know what it means, so is there a step by step process available or an update for x.org?

[https://wiki.ubuntu.com/X/Config/Resolution#Resetting]("https://wiki.ubuntu.com/X/Config/Resolution#Resetting")

---

