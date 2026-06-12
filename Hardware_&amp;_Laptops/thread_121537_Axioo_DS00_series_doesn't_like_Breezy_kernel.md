---
title: "Axioo DS00 series doesn't like Breezy kernel"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by yusenda1 on 2006-01-25
My office gave me an Axioo DS00 laptop (full specs here [http://www.axioo.net/productsDS00series.html](http://www.axioo.net/productsDS00series.html) ) which is an OEM from Clevo Co.

I've installed Hoary , than upgraded to Breezy.

There are several troubles:

1. I can't use kernel image higher than 2.6.10 series. When I try, it keep on saying "Dangerous temperature reached (2367 C). Shutting down..". The temperature shown varies between 78 C to 4678 C. I've try to recompile the 2.6.12 kernel and disabling "Machine C.. Exception", but no avail.

2. The screen is an 1280 x 800 LCD. But max in Ubuntu only 1024 x 768, more than that the screen starts scrolling.

3. Wireless can't do WPA. Tried to install ndiswrapper but doesn't work due to the kernel compiled with gcc 3.3.5 while Breezy come with gcc 4.0

4. Camera not recognized. Been trying the SCxxx camera driver, but hindered by the kernel problem.

Any help greatly appreciated!

---

