---
title: "[SOLVED] Please Help Me Diagnose What Is Wrong With My Gateway 500GR"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by 449 on 2007-12-04
Hey everyone, thanks for taking the time to help me out here. I'll try to provide as much detail as possible so just fill me in if you need something else. 

**My problem is I can't have more than the Swiftweasel web browser running without resulting in a complete system freeze. When it freezes the two lights next to the cap lock light start blinking simultaneously. I then have to force a power down and try again.**

My dad's company had a computer that had had a power surge or the HDD got erased; he's not positive though. Since the company rather just by a new machine than fix this one I am able to take it off there hands. It's a Gateway 500GR and detailed specifications for it can be found [ here ](http://support.gateway.com/s/PC/R/3724/3724sp25.shtml). The first thing I did when I got it was to check if the internal hdd was there. It wasn't. So I went ahead and installed Ubuntu 7.10 on my 250GB ex hdd. Everything worked fine until a about a month later and now I'm unable to use it for certain tasks: opening  Deluge is a guarantee freeze I have found out. It usually gets all loaded and starts downloading then a minute later will lock up. The Same thing happens with Azureus. The only time it locks up when I'm using the web browser is if the site has a lot of picture/flash type stuff(I don't know exactly what to call it.) It will even freeze when I open Rhythmbox.  I even tried disabling Compiz and just downloading one torrent and it still froze. Also when I tried to run the Mint live cd it froze there. 

So my guess would be it's hardware related ,but I have no clue how to figure out what exactly. I'd like to get this sorted out soon so I can ask for new parts for Christmas. :)

That's all the info I can think would be of help at this point ,but just ask and I'll gladly post more. Thanks!

---

### Post by Sef on 2007-12-05
Go into GRUB at start up and run the mem86test.  Run it for about 8 hours, so you know all is well.  I had a similar problem and it turned out to be the memory module on the motherboard.

---

### Post by 449 on 2007-12-05
> **Sef said:**
> Go into GRUB at start up and run the mem86test.  Run it for about 8 hours, so you know all is well.  I had a similar problem and it turned out to be the memory module on the motherboard.

How I get into GRUB at startup?

---

### Post by 449 on 2007-12-05
> **Sef said:**
> Go into GRUB at start up and run the mem86test.  Run it for about 8 hours, so you know all is well.  I had a similar problem and it turned out to be the memory module on the motherboard.

I ran the mem86 test for 8 hours and it didn't find any errors. What should I try next? Is there still a possibility that the problems with hardware? Thanks for your time.

---

