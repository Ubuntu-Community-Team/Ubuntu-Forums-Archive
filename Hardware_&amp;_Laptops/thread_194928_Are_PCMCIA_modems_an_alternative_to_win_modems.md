---
title: "Are PCMCIA modems an alternative to win modems"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by ramnarayan on 2006-06-12
Hi

Can PCMCIA card based modems be used as an alternative to the horrendous winmodems that come in most laptops.

I live in a place where internet can only be accessed via phone lines (56 kbps), Further because I use a laptop using a compatible external modem is quite a pain.

Any experiences / advise / links

will appreciate your help

thanks
ram

---

### Post by pincushionman on 2006-06-12
Short answer:
No.

Longer answer:
PCMCIA modems (also known as PC Card modems) today are almost all WinModems.  Hardware modems are a thing of the past, mostly because they get eaten frequently by lightining.  Your best bet is to do research on the modem you buy.  You'll need to know what base chipset it has.  Do not go by model numbers only - you will get burned that way.

Supported LinModem chipsets:
recent Conexant chipsets - supported for ~$15 by Linexant.com
(This includes HCF, HSF, HSF2, HSP/PCtel)
Rockwell chipsets (possibly supported by Conexant/Linexant)
PCtel (bought by Conexant)
SmartLink (smlink.com) driver that supports their modem and others, like Agere.
Agere - doesn't support Linux, see SmartLink
3com/USRobotics - hates Linux - there is almost zero support for these things. Steer clear.
Broadcom - no support (Mostly used in OEM packaging, e.g. Dell, Gateway, Compaq/HP, and certain ModemBlasters)
Intel/Ambient/Cirrus Logic - depends on model and age.

Offtopic example.  I purchased a Netgear WG511 wireless card because they were supported in Linux - prism54 chipset.  After several months of working with it and cursing, I found that mine was a v3 card, made in China.  It did not have the capability of working with the Prism firmware (not enough flashram).  To this day I do not think it is natively supported.  It may be supported by other methods, but I sold it before I found that out.

Wireless network cards are becoming more like the WinModems of yesterday.  Should we call them WinNICs or WinWireless?  Something to warn others?

Modem Resources:
[http://freewebhosting.hostdepartment.com/g/gromitkc/winmodem.html]("http://freewebhosting.hostdepartment.com/g/gromitkc/winmodem.html")
[http://linmodems.org/]("http://linmodems.org/")

---

### Post by ramnarayan on 2006-06-12
[QUOTE=pincushionman]Short answer:
No.

Longer answer:
PCMCIA modems (also known as PC Card modems) today are almost all WinModems.  Hardware modems are a thing of the past, mostly because they get eaten frequently by lightining.  Your best bet is to do research on the modem you buy.  You'll need to know what base chipset it has.  Do not go by model numbers only - you will get burned that way.

Modem Resources:
[http://freewebhosting.hostdepartment.com/g/gromitkc/winmodem.html]("http://freewebhosting.hostdepartment.com/g/gromitkc/winmodem.html")
[http://linmodems.org/]("http://linmodems.org/")[/QUOTE]

I found these links that talk a bit about compatible PCMIA cards - thats why I was curious
[http://pcmcia-cs.sourceforge.net/](http://pcmcia-cs.sourceforge.net/)
[http://www.tuxmobil.org/pcmcia_linux.html](http://www.tuxmobil.org/pcmcia_linux.html)

ram

---

### Post by pincushionman on 2006-06-12
Most likely they are win modems (because most are these days), but they reported work with linux.  Some will cost a little money for the driver, others are free.  

Unless you are connecting long distance to you ISP, WinModems/LinModems are OK.  Also, you may get better connection speeds by trying a few things:
1. Have a line test run on your line.  Shorts/Grounds/CrossedWires can seriously degrade your performance online.
2. Try connecting at your Internface box.  Your interface should be a gray box that says "Network Interface" or SBC or something on it.  You'll need a flathead screwdriver to open it up.  A cord should come out of the box and loop back in (with a standard RJ11 phone connector on it)  Plug your laptop directly into that, and see what kind of speeds you get.
3. Try connecting at someone else's house.
4. If all that doesn't help, try the PC Card modem.  First, call the company, and find out what kind of Modem bank that they use.  Most will use Agere or Conexant, but I bet there are some USR/3com boxes out there.  Find out what kind of modem the techs say people say they have the best luck with.  You may want to call a couple of times, as each tech will probably have a different opinion.

Things that will interfere with speed:
1. Pair Gain system - guaranteed to drop you speed in half.  It is a device that splits one copper pair into two using different frequencies.  This will always kill your bandwidth, and mostly you will connect at 26.4kbps.
2. A slick - kind of like a variable pair gain system.  Phone company gets around 50 lines in, and ~100 lines out.  Sometimes you can get 33.6, sometimes not.  Mostly, like above, you'll be limited to 26.4.  Depends on traffic.  
3. Rain and/or Excessive humidity.  Please don't connect during a thunderstorm (unless you like buying modems)

Remeber bits != Bytes
26.4 kbits is around 4kB/s down.
Also, you upstream is around 1/2 of your downstream (roughly), unless your ISP has the v.92 features turned on.

Finally, if you are considering Satellite, make sure you find out about the compatibility.  A lot require Windows XP because they re-write the TCP/IP stack so that it can work.  (I have seen this even with one-way Sat, but you should be able to use Internet Connection Sharing successfully).  And steer clear of one-way sat.  You want two-way, even though it will cost close to $600 for the equipment.  One-way is still tied to the phone lines, and subject to drops, lightning, etc...

---

