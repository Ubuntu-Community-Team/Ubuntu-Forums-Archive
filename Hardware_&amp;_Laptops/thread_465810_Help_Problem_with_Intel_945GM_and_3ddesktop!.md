---
title: "Help Problem with Intel 945GM and 3ddesktop!"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by 5n1p3r on 2007-06-06
i got toshiba satellite L100 and Ubuntu Dapper installed on it and i want install driver for the VGA, my laptop integrated with Intel 945 GM VGA Card, information from dxdiag my VGA has 128 memory, here the information

> 
---------------
Display Devices
---------------
        Card name: Mobile Intel(R) 945GM Express Chipset Family
     Manufacturer: Intel Corporation
        Chip type: Intel(R) Calistoga Graphics Controller
         DAC type: Internal
       Device Key: Enum\PCI\VEN_8086&DEV_27A2&SUBSYS_FF311179&REV_03
   Display Memory: 128.0 MB


and i got the driver from [http://downloadmirror.intel.com/df-support/9726/eng/dri-Intel-3.4.3006-20051209.i386.rpm](http://downloadmirror.intel.com/df-support/9726/eng/dri-Intel-3.4.3006-20051209.i386.rpm) and i used alien to convert it to debian package!

but after reboot look like the driver doesn't affect the card, i already add

> 
VideoRam 131072


but from information i got from logfile i'm only got 77 Mbyte, here the information

> 
(--) I810(0): Maximum frambuffer space: 7784 kByte
(--) I810(0): Maximum space available for video modes: 7784 kByte


and one more question, i got problem with 3ddesktop, when i activated the daemon, it always exit and this error message appear

> 
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.


can anybody here solve my problem. thank before!

---

### Post by renzokuken on 2007-06-06
i think the correct driver is in the repos. called something like xserver-xorg-intel. cant honestly remember the exact name

---

### Post by Atomic Dog on 2007-06-06
Open Synaptic Pkg Mgr and just do a search for "intel" and you'll find it on the list.

---

### Post by Espionage724 on 2007-06-11
Yep try the driver thats included in the package manager. Also u may want to get 915resolution to have ur display better if u didnt download it already.

---

