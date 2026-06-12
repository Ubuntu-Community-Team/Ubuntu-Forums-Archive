---
title: "Jumpy mouse"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by Akegata on 2007-03-07
I have a really annoying problem.
Whenever my hard drive is under heavy usage, my mouse will stop working for short periods of of time. It might stop for half a second, then work two seconds, stop one second and so on.

I have a MX Revolution now, but the problem was there when I used my old MX 700 as well.
The problem is there both when I use the Revolution configured like I want it and when it's configured as a standard USB mouse.

lspci -v | grep SATA gives me
```
00:05.0 IDE interface: Silicon Integrated Systems [SiS] 182 SATA/RAID Controller (rev 01) (prog-if 85 [Master SecO PriO])
```
Are there any known issues with this chipset? I can't find anything when I search for it anyways.

sudo hdparm -tT /dev/sda gives me
```
/dev/sda:
 Timing cached reads:   2416 MB in  2.00 seconds = 1206.55 MB/sec
 Timing buffered disk reads:  200 MB in  3.00 seconds =  66.61 MB/sec
```

Any help with fixing or troubleshooting this would be great.

---

