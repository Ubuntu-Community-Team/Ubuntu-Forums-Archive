---
title: "DPMS doesn't work on fglrx"
date: 2012-07-23
forum: Hardware
---

### Post by donbowman on 2012-07-23
I have an ATI/AMD Radeon HD 7950:
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Tahiti PRO [Radeon HD 7950] (prog-if 00 [VGA controller])
        Subsystem: Giga-byte Technology Device 254c
        Flags: bus master, fast devsel, latency 0, IRQ 57
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f0200000 (64-bit, non-prefetchable) [size=256K]
        I/O ports at 2000 [size=256]
        Expansion ROM at f0260000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx

I am running 12.04 with a slightly upgraded kernel from ppa mainline:
$ uname -a
Linux server 3.3.7-030307-generic #201205211535 SMP Mon May 21 19:36:02 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

When i allow the monitors to go to sleep, they leave their backlight on. When i force them to sleep (xset dpms force standby), they go black and come back.

In the dmesg, these lines appear whenever going into DPMS off (either by letting it idle or by forcing it):

[168677.427966] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[168686.116851] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=0
[168686.116868] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[168686.121587] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=1
[168686.121601] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[168686.412854] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1

it seems that it detects an event.

My 2 monitors are plugged into the DisplayPort [first one near top of card] and the DVI. The HDMI is not plugged in.

I am running fglrx 2:8.960-0ubuntu1, fglrx-amdcccle 2:8.960-0ubuntu1, xvba-va-driver 0.7.8-1ubuntu3.

I am running xorg 1:7.6+12ubuntu1

I do not have the xorg swat or edgers ppa install. its just from the stock.

I tried switching from the DVI port to the HDMI for the second monitor, same affect.

Can anyone suggest a debugging technique? I'd really like DPMS to work [it was working until yesterday when i swapped my nvidia GT 240 for this fancy beast). The graphics card is a GV-R795WF3-3GD.

---

### Post by donbowman on 2012-12-09
I finally found a workaround (for posterity and others):

What is happening is that when the DPMS kicks in, the (DisplayPort-connected) monitor trips its 'auto input search'. This in turn disconnects the DisplayPort to try e.g. HDMI or DVI, which in turn causes a hot-plug event, which in turn wakes up the DPMS.

The workaround for me was to change the monitor (using its OSD) to manual input selection.

Now DPMS works.

This is only for the DisplayPort-connected monitor, the DVI one is fine.

---

