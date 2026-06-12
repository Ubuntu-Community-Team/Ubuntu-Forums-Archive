---
title: "Lenovo Thinkpad W520 Docking Station troubles"
date: 2011-08-29
forum: Hardware
---

### Post by Evonus on 2011-08-29
Hey guys, I'm using a Ubuntu 11 partition on my Lenovo W520 thinkpad. 

The default OS is Windows 7, and when I boot up using Windows 7, the computer recognizes the docking station only when I get to the loading screen. Before that my monitor keeps flashing on and off saying that it's trying to connect. 

When I try to boot up using my Ubuntu partition, the laptop doesn't recognize the monitor. 
[This]("http://www.google.com/products/catalog?q=dell+24''+monitor&um=1&ie=UTF-8&tbm=shop&cid=17507504734673578407&sa=X&ei=kBRcTobBC-3K0AGLwfzSBg&ved=0CGsQ8gIwBA") is my monitor in case that helps.

The laptop works just fine when I run it without the docking station in either Windows 7 or Ubuntu.

I'll take any and all suggestions!

---

### Post by DPUkyle on 2011-10-04
Hi Evonus.

I suspect the trouble is not based in the docking station, but in the graphics card.

I too have a Lenovo W520 with an NVIDIA Quadro 1000M graphics card.  This card uses Optimus technology to switch between the built-in Intel graphics and the more powerful (but battery-draining) accelerated NVIDIA chip.  Unfortunately Optimus, and NVIDIA as a whole, is famously unsupportive of any non-Microsoft OS.

You may try opening the BIOS and disabling NVIDIA Optimus there, however it seems that the built-in Intel graphics are too weak to run external monitors.  You might also try using a DisplayPort cable (or DP-to-DVI) to connect not via to docking station but on the laptop directly.

Good luck and let us know if you have success - I'm dying to get Windows off of this machine but haven't gotten dual external monitor support working yet.  Fingers crossed...

---

### Post by xgorosito on 2011-10-07
Hi Guys,

Did you got the sound working?

Thanks!

---

### Post by diffuser78 on 2012-05-11
Is there any update to this thread ? I have a thinkpad W520 and running 12.04. The monitor's are not identified and I am unable to use my dual monitors using the docking station.

Can someone please help ?

Thanks.

---

### Post by Janir on 2012-05-21
NO update but I can confirm I have the exact same problem.  Laptop works just fine when undocked, but the dock wil not see any video at all.

---

