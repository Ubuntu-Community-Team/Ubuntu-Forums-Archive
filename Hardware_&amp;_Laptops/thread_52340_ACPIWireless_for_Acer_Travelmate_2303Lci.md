---
title: "ACPI/Wireless for Acer Travelmate 2303Lci"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by AdeptPaladin on 2005-07-27
First and foremost.. THANK YOU FOR BROADCOM SUPPORT!

That has been my biggest issue with any Linux distro I used; no network capacity out of the box so I could get the changes/help/etc I needed in order to get all the problems sorted out.  As we speak, I'm sitting in Firefox in Ubuntu and am rather pleased.

Two issues that I'd like to have sorted out though and then I'll be cruising. 

First, ACPI.  Is it possible to control CPU speed, suspend, and such?  I can see a hibernate option.. but when I add the 'CPU Frequency Monitor', it doesn't seem to recognize the CPU.  Nor do I see an option to reduce the speed.

Second, my wireless.  This beast uses an IPN2220 802.11b/g integrated wireless LAN card.  Try as I might, I can't get it to work.  I know I need to use ndiswrapper, but even when that succeeds I still can't connect to my home network.

Please also bear in mind that I am a complete neophyte on linux.. as I stated above, this is my first successful install :p

---

### Post by AdeptPaladin on 2005-07-27
[QUOTE=cpuinfo]processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Celeron(R) M processor         1500MHz
stepping        : 5
cpu MHz         : 1498.728
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe
bogomips        : 2973.69[/QUOTE] 
Just in case that helps.. still trying to find out how to get the powernowd to work as well as to get the battery recognized.

---

