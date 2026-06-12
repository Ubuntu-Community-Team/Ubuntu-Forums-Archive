---
title: "US Robotics 802.11g on Toshiba Satellite 2410"
date: 2006-03-13
forum: Hardware &amp; Laptops
---

### Post by nomenklatura on 2006-03-13
Ok, so I've checked all the forums, I've checked loads of sites, I've wasted hours of my time, and even some money. So for future reference here is a tip for those of you thinking of getting a US robotics 802.11g wireless card (USR5410) on a toshiba satellite 2410 laptop: Don't. 

This is the kind of stuff that makes me crave for anything that isn't linux. The documentation is poor, if not downright misleading. This ndiswrapper thing is a piece of crapware if ever I've seen one. US robotics claim to be reaching out to the linux community, when all they do is post a link to linuxant. Of course, Linuxant gives no clues to the uninitiated on how to get whatever it is they make working. And when you do get it to work, the .inf files (drivers) don't work anyway. 

So save yourself a lot of time and aggro, get yourself the cheapest, oldest 54 Mbit piece of metal you can find (eg Netgear stuff, possibly second hand). That *will* work.

Of course, if anyone does know how to get the USR card to work, then *please* let us poor idiots down here know....

---

### Post by Zelut on 2006-03-13
I'd like to try & help you get your wireless working.  I've actually had great success with the ndiswrapper so far (although I haven't dealt with your card).  If you're willing to keep trying... I hate to let a problem beat me :)

I'm willing to look a little deeper into it if you can give me the output of:
**lspci | grep 802.11**
or (if no results)
**lspci | grep Wireless**

Also the output of **lspci -n**

---

### Post by nomenklatura on 2006-03-14
Thanks for your reply. My post was a result of much exasperation.

lspci | grep 802.11 gave no output.

lspci | grep Wireless gave

```
0000:03:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

```

lspci -n gave:

```
0000:00:00.0 0600: 8086:1a30 (rev 05)
0000:00:01.0 0604: 8086:1a31 (rev 05)
0000:00:1d.0 0c03: 8086:2482 (rev 02)
0000:00:1d.1 0c03: 8086:2484 (rev 02)
0000:00:1e.0 0604: 8086:2448 (rev 42)
0000:00:1f.0 0601: 8086:248c (rev 02)
0000:00:1f.1 0101: 8086:248a (rev 02)
0000:00:1f.5 0401: 8086:2485 (rev 02)
0000:00:1f.6 0703: 8086:2486 (rev 02)
0000:01:00.0 0300: 10de:0175 (rev a3)
0000:02:08.0 0200: 8086:1031 (rev 42)
0000:02:0b.0 0607: 1179:0617 (rev 32)
0000:02:0b.1 0607: 1179:0617 (rev 32)
0000:03:00.0 0280: 104c:9066

```

Hope this helps us get somewhere....

---

### Post by Zelut on 2006-03-15
Ok check out this link.  Its a list of drivers for your chipset, [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Special:Search?search=104c%3A9066&fulltext=Search](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Special:Search?search=104c%3A9066&fulltext=Search)

this is what you want to search for on those pages: 104c:9066

download one of those drivers, get a copy of the .inf & .sys file & let me know.

---

### Post by nomenklatura on 2006-05-11
Nothing doing, won't go, at least not with the amount of effort I'm prepared to put into it. Switched to an old netgear card instead, which works.

---

### Post by aeroRunner on 2006-05-18
kuyaedz, I'm not ready to give up yet, I just need a little help if you are still willing.  I did what you said and found my card in the list

Card: US ROBOTICS USR805417 802.11g MaxG PC Card

    * Chipset: Broadcom Corporation BCM4318 (rev 02)
    * pciid: 14e4:4318
    * Driver: You have to unshield the file Data.exe and then the file data2.cab. These files are on the install CD, or can be downloaded[52]. Tested with the driver USRMAXGa.inf on Slackware 10.1, kernel 2.4.29, ndiswrapper 1.5

I spent hours following the ndiswrapper directions and never got it to work.  But, hopefully I was just missing something.  I have USRMAXGa.inf and bcmwl5.sys extracted already.  There is also a USRMAXG.inf but I don't know what the difference is.

So, what should I do now?
Thanks

edit: I see this was posted in a Breezy forum.  I am actually using Dapper.

---

