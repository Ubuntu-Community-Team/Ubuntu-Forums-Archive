---
title: "Epson DX7400 printer and scanner"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Genius2000 on 2007-10-31
Hi, someone knows where can I find Epson DX7400 drivers?

I alrady try here: [http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html) but there aren't.

Thanks in advance, Andrea

---

### Post by l33t_3lv3n_g33k on 2007-10-31
Epson lists a linux driver for your printer.  Not sure how well it will work since the file size reported by the website is 0.00 bytes...
 
Here's the link: [Epson DX7400]("http://esupport.epson-europe.com/ProductHome.aspx?lng=en-GB&data=lkuCfcvA9cwxk62Z0ec7JtnKga5lQZcczfcUfkYzQzwU003D&tc=6")
 
If the link doesn't work, just go to the Epson website and search for drivers for your printer.  Be sure to list Linux as your OS.
 
Alternately, there is an entry at [LinuxPrinting.org]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX7400")

---

### Post by Genius2000 on 2007-10-31
> **l33t_3lv3n_g33k said:**
> Epson lists a linux driver for your printer.  Not sure how well it will work since the file size reported by the website is 0.00 bytes...
 
Here's the link: [Epson DX7400]("http://esupport.epson-europe.com/ProductHome.aspx?lng=en-GB&data=lkuCfcvA9cwxk62Z0ec7JtnKga5lQZcczfcUfkYzQzwU003D&tc=6")
 

Hi, many thanks for your very prompt reply, this file is not a driver, but simply a html file with the link I provided before...

> 
If the link doesn't work, just go to the Epson website and search for drivers for your printer.  Be sure to list Linux as your OS.


Done, but whit no results

> 
Alternately, there is an entry at [LinuxPrinting.org]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX7400")


I already installed gutenprint but DX7400 is not supported

Regards, Andrea

---

### Post by boris64 on 2008-03-08
Printig work with DX4800 driver, but colors are not corect

---

### Post by Genius2000 on 2008-03-08
I already noticed, tankyou.

Andrea

---

### Post by susanpenter on 2008-03-12
I have got mine printing using cups and selecting the CX7400 which uses the same drivers.  Unfortunately I haven't worked out how to install the scanner drivers.

Hope that helps,

Susan

---

### Post by Hopottinix on 2008-03-23
Epson stylus DX7400 is working fine here after installing the linux drivers from Avasys: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

The .rpm package was converted to .deb with alien and the driver installed just fine. Note that I only installed the "printer driver" and have only tried printing stuff.

The printer driver for CUPS by the way.

---

### Post by Bou on 2008-05-30
Just for the record - I managed to make my DX7400 work (printer AND scanner) properly by following this howto:

[http://forum.ubuntu-it.org/index.php?topic=142737.msg951555](http://forum.ubuntu-it.org/index.php?topic=142737.msg951555)

It's in Italian; I don't really speak Italian but it's quite similar to Spanish, so it was not too hard to understand most of it. If anyone buys one of these and needs to follow the howto but doesn't understand it or something, please PM me and I'll translate it.

Cheers :)

---

### Post by iamthesun on 2008-06-07
> **Genius2000 said:**
> Hi, someone knows where can I find Epson DX7400 drivers?

I alrady try here: [http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html) but there aren't.

Thanks in advance, Andrea
I went to the Epson website and downloaded the drivers from there...
[http://esupport.epson-europe.com/ProductHome.aspx?lng=en-GB&data=lkuCfcvA9cyGlxkS+hCB15owoYA0zhHaWRLdhFhZGMkU003D&tc=6](http://esupport.epson-europe.com/ProductHome.aspx?lng=en-GB&data=lkuCfcvA9cyGlxkS+hCB15owoYA0zhHaWRLdhFhZGMkU003D&tc=6)
Select Epson scan (3.2a)

Hope it works for you too.

---

