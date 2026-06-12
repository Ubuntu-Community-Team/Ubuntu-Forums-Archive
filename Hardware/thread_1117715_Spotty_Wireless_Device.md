---
title: "Spotty Wireless Device"
date: 2009-04-06
forum: Hardware
---

### Post by d3railur on 2009-04-06
Hi, new member of this community and having the first problem my own resolve/google searches cannot solve.

I am running the latest 64 bit Ubuntu (8.10).  
My wireless device is hit or miss.  It seems it will 'work' every other time I boot into Ubuntu.

The device previously worked every time, and it works with the USB bootable version of Ubuntu I use in a pinch, so I know it is not a compatibility issue.

The start of the problem coincided with a video driver upgrade.  I upgraded to 'nvidia-glx-180-dev'(and all the others that went with it - 180-kernel-source etc) via the synaptic package manager.

The first time I rebooted after installing this driver resulted in an error before fully loading into Ubuntu.  I do not remember the exact verbage of the error but I was given options that read something like "Run Ubuntu in Low-Graphics Mode", "Return to a Previous Setting" etc. 

lshw -C network yields for my wireless device:
 
 *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wmaster0
       version: 00
       serial: xx.xx.xx.xx.xx.xx (I removed this because I am paranoid)
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=xx.xx.x.xxx (paranoia again)
       latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

Obviously all is well right now since I am posting on the internet.  However, when it does not work the first line looks like this:

*-network DISABLED

Based on all the searching I have done it appears to be a driver issue with the wireless device.  But I do not know how to fix it.  Based on the fact that it works sometimes and does not work other times, it appears there is a backup setting that Ubuntu defaults to that causes it to work (or maybe not?!?!)

Any advice out there on what I can do to stabilize this problem?

Thanks in advance.

---

### Post by d3railur on 2009-04-06
Another thought, could this be a problem with the permissions?

---

