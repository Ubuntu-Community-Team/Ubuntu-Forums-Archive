---
title: "Random questions again"
date: 2016-03-14
forum: Hardware
---

### Post by KayeNg on 2016-03-14
Hello guys.  Apologies if this is not the right forum.

1. I have a really old desktop computer that I brought back to life by installing Lubuntu in it.  There are four USB port at the back.  Three were being used, including a Tenda wifi adapter. I then plugged in flash drive.  Within 5 to 15 minutes, the Tenda wifi adapter was toast (not the newly plugged-in flash drive).  Any theories?

2. I have another old desktop computer.  The RAM is 1 gb DDR2. I went to a computer store and asked for a DDR2, but the attendant asked me something that I didn't understand.  All I remember is that he said I can buy one from them and it would fit in the slot, but the computer may not recognize it and it may not be utilized. So I have to find out something first about the RAM.  In short, I thought mentioning something like DDR2 or DDR3 is sufficient when buying RAM. Can anyone enlighten me please? What am I suppose to look (before I go back to the store)?

---

### Post by v3.xx on 2016-03-14
Yep. the manufacture has set (built in) a ram limit.  Whats the specs on this box?

```
inxi -b
```

---

### Post by KayeNg on 2016-03-15
Thanks v3.xx
Here it is:
> System:    Host: 01-lubuntu Kernel: 3.19.0-49-generic i686 (32 bit) 
           Desktop: LXDE (Openbox 3.5.2) Distro: Ubuntu 14.04 trusty
Machine:   Mobo: N/A model: Wolfdale1333-D667. Bios: American Megatrends version: P1.40 date: 03/14/2008
CPU:       Single core Intel Celeron CPU 430 (-UP-) clocked at 1795.025 MHz 
Graphics:  Card: Intel 82945G/GZ Integrated Graphics Controller 
           X.Org: 1.17.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@59.8hz 
           GLX Renderer: Mesa DRI Intel 945G x86/MMX/SSE2 GLX Version: 1.4 Mesa 10.5.9
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller driver: r8169 
           Card-2: Linksys AE2500 802.11abgn Wireless Adapter [Broadcom BCM43236] driver: ndiswrapper 
Drives:    HDD Total Size: 1031.2GB (2.0% used)
Info:      Processes: 144 Uptime: 13 min Memory: 346.6/992.8MB Client: Shell (bash) inxi: 1.9.17 


---

### Post by v3.xx on 2016-03-15
Here's my findings..

Page 16
[http://www.asrock.com/MB/Intel/Wolfdale1333-D667/index.asp?cat=Manual](http://www.asrock.com/MB/Intel/Wolfdale1333-D667/index.asp?cat=Manual)

About max ram
[https://www.google.com/search?client=ubuntu&channel=fs&q=wolfdale1333-d667+max+ram&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=wolfdale1333-d667+max+ram&ie=utf-8&oe=utf-8)
This answer varies from 512M to 4G.  Your going to have to sort this out.

---

### Post by coldraven on 2016-03-15
It says 4GB max on the Crucial site. (DDR2 UDIMM). Maybe best to take the existing memory to the store, wrap it in an anti-static bag.
[http://www.crucial.com/usa/en/compatible-upgrade-for//wolfdale1333-d667](http://www.crucial.com/usa/en/compatible-upgrade-for//wolfdale1333-d667)

---

### Post by KayeNg on 2016-04-11
Thanks guys.  According to this [URL="http://www.asrock.com/mb/intel/wolfdale1333-d667/"]http://www.asrock.com/mb/intel/wolfdale1333-d667/

> Supports Dual Channel DDR2 667/533 x 2 DIMM slots with max. capacity up to 4GB
[/URL]

...now looking at the compatible RAMS in this page --> [URL="http://www.crucial.com/usa/en/wolfdale1333-d667/CT771046"]http://www.crucial.com/usa/en/compatible-upgrade-for//wolfdale1333-d667
[/URL]
...the fourth one 
**CT771046**

it says 
**[Crucial 2GB DDR2-666 UDIMM                                                                                                      ]("http://www.crucial.com/usa/en/wolfdale1333-d667/CT771046")**

............but the asrock website says DIMM, not UDIMM. Is it compatible or not?

and how do I know if the one currently installed is dimm or udimm?

---

