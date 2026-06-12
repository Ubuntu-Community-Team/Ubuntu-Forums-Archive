---
title: "ATI display chipset vs Nvida display chipset"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by adrianmak on 2007-11-24
I knew that Nvida display card can work smoothly onm Linux especially compiz fusion, beryl visual effects enabled. I also knew that ATI has released a latest version of driver for Linux. Then can i use newer ATI display card like 2000 series or 3000 series to use compiz fusion, berly visual effetcs ?

ATI display driver for linux  mature enough to run these visual effects ? or Just stay on very old ati display card like 9200 ATI 128, etc.

---

### Post by catfishk on 2007-11-25
i use both chipsets regularly and IMO the Nvidia drivers are less of a hassle.  however, AMD/ATI has definitely come a long way this past year in supporting us Linux users and their drivers are becoming up to par with Nvidia

 on my Thinkpad i run the binary AMD/ATI fglrx driver v 8.42.3 (not the Ubuntu xorg-driver-fglrx) along with Compiz-Fusion under AIGLX.  until recently the fglrx driver did not support AIGLX and us Linux users had to use a dated XGL implementation to achieve beryl/compiz effects, that was sort of a hack and didn't enable us to use accelerated programs (games, etc) within the desktop environment while running XGL.  in a short sense, it sucked
 the latest releases of the AMD/ATI fglrx driver run well using hassle-free AIGLX and, aside from a few clipping issues i have had, work very well.  there is no doubt in my mind that the next fglrx releases with solve these few performance issues

 i am unsure if the fglrx driver will run as well with a newer card than my X1300, but i believe it would

 good luck!

---

### Post by Yellow Pasque on 2007-11-25
In my opinion, the latest ATI drivers are not stable enough for most people. There are major issues with screen corruption, memory leaks, and poor performance. Nvidia's not perfect either, but their drivers perform much better. The open-source ATI drivers have some 3D acceleration for older cards though, so that's something to consider.

AMD/ATI has begun opening up the specs so that the open-source community can build a real Linux driver. Nvidia shows no sign of releasing any specs, so anyone trying to write an nvidia driver will be forced to reverse engineer.

So if Compiz is important to you and you want to run it right now, get an nvidia card (preferably not an 8xxx series) or an older ATI card. ATI has dropped support for 9200 and below in their latest driver releases, so don't get anything less than a 9500 if you want to have the option of running the proprietary driver. But don't get anything newer than the R400 chip cards, i.e. no Radeon X1K or 2kHD cards if you want to be able to have eye candy with the open source driver.

---

