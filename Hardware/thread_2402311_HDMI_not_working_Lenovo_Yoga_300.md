---
title: "HDMI not working Lenovo Yoga 300"
date: 2018-09-28
forum: Hardware
---

### Post by oshah on 2018-09-28
Hi,

Recently installed Ubuntu 18.04 on my Lenovo Yoga 300.
The HDMI port isn't working. I also can't change the brightness of my main display. I think these issues are related; I read another post saying that these problems were solved together.

UPDATE:
I booted from a live usb and everything seems to work fine. The VGA driver is i915, which seems to be loaded fine; I tried removing and reloading it with modprobe to no avail.

xrandr:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1366 x 768, current 1366 x 768, maximum 1366 x 768
default connected primary 1366x768+0+0 0mm x 0mm
   1366x768      76.00* 

lshw:
*-display UNCLAIMED
             description: VGA compatible controller
             product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:2050(size=8) memory:c0000-dffff

lspciL
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)
00:13.0 SATA controller: Intel Corporation Atom Processor E3800 Series SATA AHCI Controller (rev 0e)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 0e)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0e)
00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 1 (rev 0e)
00:1c.1 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 2 (rev 0e)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation Atom Processor E3800 Series SMBus Controller (rev 0e)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
02:00.0 Network controller: Intel Corporation Wireless 3160 (rev 93)

Please help me.

Omar

---

### Post by oshah on 2018-10-06
Solution:
- My system was randomly freezing; I fond that changing 'quiet splash' to 'nomodeset' in /etc/default/grub and running update-grub fixed that issue.
After several re-installs, I found that the same change broke the brightness and hdmi port.
Apparently it's an issue with the Intel Bay Trail graphics gubbins, and can be fixed by instead replacing 'quiet splash' with 'quiet splash intel_idle.max_cstate=1'.
Woo!

---

