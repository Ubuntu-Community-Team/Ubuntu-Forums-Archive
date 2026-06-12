---
title: "Change the plate?"
date: 2017-10-02
forum: Hardware
---

### Post by padaenriqueidey on 2017-10-02
Hi, good to see who can help me. I have the following desktop computer:
- 500 GB hard drive
- Motherboard Asus M2N ATX AMD AM2
- Micro Amd Athlon 64 X2 6000 (3000 Mhz) 2Mb dual core
- Graphics card Nvidia GF 210 1Gb DDR3 64 bits
- Memory Kingston 4 Gb DDR2 800 Mhz
- Power supply 350 w
According to the plate I have, the maximum processor it supports is 6400 (3200 Mhz).
I use Ubuntu from version 10.04 and until 14.04 with this pc I supported it, but for a few months I have observed that I think it lacks a processor (version 16.04 I had to uninstall because it was hard to start and stop). Is it time to change the board, because if you change the micro in a short time and will not support future versions of Ubuntu?
Thank you.
Greetings.

---

### Post by deadflowr on 2017-10-02
> Is it time to change the board, because if you change the micro in a short time and will not support future versions of Ubuntu?
I'm sure the existing processor will be supported for quite a while.
Same goes for the prospective upgrade.

What you might do it open up the case and do a hard inspection of the internals and see if anything looks burned out and/or run some basic tests on the machine 
such as smart tests
[https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")
or memtests
[https://askubuntu.com/questions/591488/how-do-i-run-memtest86]("https://askubuntu.com/questions/591488/how-do-i-run-memtest86")

You may also double check that everything is properly seated, such as the gpu and the ram sticks.

---

### Post by efflandt on 2017-10-03
I have an HP PC from 2004 with the first Athlon64 3200+ (1 core, 2.0 GHz) with I think is 2 GB PC-3200 RAM and legacy ATI X1300 AGP graphics. It has WinXP and both 32 and 64-bit Ubuntu 10.04 on its hard drive, but I was able to boot and run 64-bit Ubuntu 16.04 on it installed on SD card without any problems. And it is missing at least one instruction that newer 64-bit CPU's have (lahf_lm). Its PSU was upgraded to 330 watts, because its overrated HP OEM 250 watt PSU could not even boot 130 watts max (measured AC input after PSU upgrade). So whatever your issue is might not be Ubuntu, it might be failure of some hardware.

However, I did have an issue with 16.04 (only on my main PC from 2010) which was running a conventional, but old, i5 650 with Nvidia GTX 1060 graphics. My PC would NOT display "any" text during boot (blank screen through BIOS splash and grub menu) until something did graphics (gui login), from that point on everything worked fine. I did not have that issue with 16.10 (which has now reached end of support) or any other computer (even older). So I need to test this PC with most recent 16.04.3 or upgrade to short term 17.04.

---

### Post by padaenriqueidey on 2017-10-25
In the end I changed the plate, the micro and the memory and goes to perfection.

---

