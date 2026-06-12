---
title: "Windows 7 RC 2100 32-bit + Virtual PC 2007 + Ubuntu 9.04 32-bit"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by patrickalexson on 2009-07-18
**System Specifications:**

Time of this report: 7/18/2009, 22:01:38
       Machine name: RATPCG
   Operating System: Windows 7 Ultimate 32-bit (6.1, Build 7100) (7100.winmain_win7rc.090421-1700)
           Language: English (Regional Setting: English)
System Manufacturer: Acer           
       System Model: Extensa 5620                   
               BIOS: Ver 1.00PARTTBL
          Processor: Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz (2 CPUs), ~1.7GHz
             Memory: 1536MB RAM
Available OS Memory: 1526MB RAM
          Page File: 1589MB used, 1463MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 11

 Card name: Mobile Intel(R) 965 Express Chipset Family
       Manufacturer: Intel Corporation
          Chip type: Mobile Intel(R) 965 Express Chipset Family
           DAC type: Internal
         Device Key: Enum\PCI\VEN_8086&DEV_2A02&SUBSYS_011F1025&REV_03
     Display Memory: 358 MB
   Dedicated Memory: 0 MB
      Shared Memory: 358 MB
       Current Mode: 1280 x 800 (32 bit) (60Hz)
       Monitor Name: Generic PnP Monitor
      Monitor Model: unknown
         Monitor Id: SEC3945
        Native Mode: 1280 x 800(p) (60.004Hz)
        Output Type: Internal
        Driver Name: igdumdx32.dll,igd10umd32.dll
Driver File Version: 8.15.0010.1825 (English)
     Driver Version: 8.15.10.1825
        DDI Version: 10
       Driver Model: WDDM 1.1
  Driver Attributes: Final Retail
   Driver Date/Size: 6/16/2009 18:26:08, 536576 bytes

**Virtual Machine Specifications:**

Allocated Ram: 777mb
Allocated Space: ~16GB

**Problem/Issue:**

This is the readout that is displayed when trying to
boot into either normal or Live CD mode with VPC2007:

[IMG]http://www.rockwallsahm.com/screenshot.png[/IMG]

Any suggestions as to what to try?

Thanks!

---

### Post by patrickalexson on 2009-07-19
Well it seems I was able to fix the issue. Thought it was something rare applying to just my setup but thanks to the info here:

[http://nemesisv.blogspot.com/2009/04/installing-ubuntu-904-on-microsoft.html](http://nemesisv.blogspot.com/2009/04/installing-ubuntu-904-on-microsoft.html)

All I had to do was:

Boot Ubuntu 9.04 up. On the first screen, choose [English].
Then press [F4] and select [Safe Graphics].
Then press [F6], but do not select any option. Instead press [Escape] and it will allow you to change the command line. Remove the option "quiet splash --" and replace it with "vga=791 noreplace-paravirt" instead.
Press [Enter] to start the installation.



It did take a minute to boot but its working now. Now I will see if I can install it properly.


It looks like this fix will work with anyone having the same issues.

---

