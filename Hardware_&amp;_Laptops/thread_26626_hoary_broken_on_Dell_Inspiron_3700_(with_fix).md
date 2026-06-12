---
title: "hoary broken on Dell Inspiron 3700 (with fix)"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by stefankluth on 2005-04-13
Hi,

after a successful upgrade from warty to hoary on my Dell inspirion 3700 I tried the install from scratch expecting this to work fine.  Here is my story:

1) installer runs fine and detects all hardware (impressive)

2) install runs fine, reboots ok into new system

3) installation of packages runs fine until Xorg is installed
    the switch to vt7 messes up the display, switching back to vt1 does not help as   
    the console is messed up too -> reboot

4) in recovery mode dpk-reconfigure xserver-xorg does not help; I tried various ways 
    to specify things but nothing helped.

5) starting the ubuntu live system reveals the same problem

system unuseable?  Knoppix comes to the rescue

6) start knoppix (3.6) and copy the modelines from knoppix XF86config into the    
    monitor section of xorg.conf:

Section "Monitor"
        Identifier      "Dell TFT"
        Option          "DPMS"
        HorizSync    28.0 - 78.0 # Warning: This may fry very old Monitors
#       HorizSync    28.0 - 96.0 # Warning: This may fry old Monitors
#       VertRefresh  50.0 - 75.0 # Very conservative. May flicker.
        VertRefresh  50.0 - 62.0 # Extreme conservative. Will flicker. TFT default.
        #  Default modes distilled from
        #      "VESA and Industry Standards and Guide for Computer Display Monitor
        #       Timing", version 1.0, revision 0.8, adopted September 17, 1998.
        #  $XFree86: xc/programs/Xserver/hw/xfree86/etc/vesamodes,v 1.4 1999/11/18 16:52:17 tsi Exp $
        # 640x350 @ 85Hz (VESA) hsync: 37.9kHz
        ModeLine "640x350"    31.5  640  672  736  832    350  382  385  445 +hsy

...

7) shut down knoppix and reboot; display works!

If somebody is interested I can supply various logfiles to debug the problem.  I have never succeeded to understand which modeline was picked after all from the X logs ....

Cheers, Stefan

---

