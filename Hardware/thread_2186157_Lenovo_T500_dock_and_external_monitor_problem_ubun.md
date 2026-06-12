---
title: "Lenovo T500 dock and external monitor problem ubuntu 13.10"
date: 2013-11-06
forum: Hardware
---

### Post by margus-pala on 2013-11-06
Hi

My docking station external monitor sometimes works and sometimes not. I remember having a few such cases with previous T61 laptop also. Can anyone advise how to debug the situation?

For example I boot up the laptop and only built in display works. Sometimes external monitor starts to work when I:
a) just open System settings>Displays 
b) undock and redock
c) sleep and unsleep
d) reboot

Often none of these actions have no effect and then suddenly the external monitor starts to work again. How to make the monitor work every time?

I am pasting there a few system information snippets
# xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 32767 x 32767
LVDS1 connected primary 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+   50.1  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

# lspci -v
...
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 20e4
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f4400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Kernel driver in use: i915
...

---

### Post by margus-pala on 2013-11-06
I did some additional experiments as I had additional docks and laptops laying around. 

I tested another dock and still external display did not work with DVI digital.
I tested another lenovo T61 laptop and still external monitor did not work.

However the very same external monitor works when I use VGA analog connection instead of digital DVI. Too bad that the picture is visibly more blurry over analog connection.

It possible that problem can be related to my LG W2453 display, too bad I dont have another DVI monitor laying around right now....

---

### Post by tgalati4 on 2013-11-06
I have a T43p and I have found that my dock was sensitive to different DVI displays.  I believe it has to do with the timing of the handshaking between the graphics card (through the dock) and the display--sending resolution and timing parameters.  Try using *gtf* to get the modeline for the display when it is hooked up and running correctly.  Then put that modeline in xorg.conf and see if that helps.  You would need to put it in the "Screen 2" or "Display 2" section.

tgalati4@Mint14-Extensa ~ $ gtf 1920 1080 60

  # 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
  Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync

Understand that the docks were designed before the latest generation of TV's/flat panel displays, so there may be some internal signal losses for higher resolution/higher frequency displays.  That would be consistent with intermittant behavior.

Try differernt/better cables, and as you have suggested, find another display to test with.

---

