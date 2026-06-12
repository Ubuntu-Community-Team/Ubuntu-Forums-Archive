---
title: "Dial-Up Ubuntu x64 Conexant Modem"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by whos2know on 2007-09-02
Hi, 

I am using Ubuntu 7.10 x64 version and I'm over at my moms house.  She only has Dial Up and I want to be able to Dial out with my modem but I can't get my modem to work.  Linux seems to see it being there in the Hardware profile...but that is about it... please help.  I am really new with linux but I am really impressed with it too and would like to continue  to use linux and load it up on my mothers computer as well... thank you!!!

---

### Post by eggdeng on 2007-09-02
Linuxant [http://www.linuxant.com/drivers/]("http://www.linuxant.com/drivers/") do pretty good support for these, the hitch being that they charge for the full 56K driver. They do a free 14.4K version though, which is good enough if you're stuck.

---

### Post by jrcanedo on 2007-09-03
Please visit the Dell's Forum Site, there were free drivers for your modem, it's an oem conexant modem drivers for Ubuntu 7.04. It will offer a full 56kbps speed and you don't need to pay for that driver from linuxant. The good thing is that you are not going recompile it, all you have to do is to install it right away.

Good luck!

---

### Post by YvesDL on 2007-09-03
> **jrcanedo said:**
> Please visit the Dell's Forum Site, there were free drivers for your modem, it's an oem conexant modem drivers for Ubuntu 7.04. It will offer a full 56kbps speed and you don't need to pay for that driver from linuxant. The good thing is that you are not going recompile it, all you have to do is to install it right away.

Good luck!
Looked everywhere in Dell's Forum. Can't find it. Help!

---

### Post by whos2know on 2007-09-04
I haven't tried it yet but I think this is the driver.  Here is the link!!!

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)

---

### Post by whos2know on 2007-09-05
Well... I tried to install the driver.... but I don't get any response to if it is working.... I am really new at this and anyone knows how to help me get this working it would be great thank you!!! :)

---

### Post by YvesDL on 2007-09-20
> **whos2know said:**
> Well... I tried to install the driver.... but I don't get any response to if it is working.... I am really new at this and anyone knows how to help me get this working it would be great thank you!!! :)

Well I tried it too. And it works just fine! Full speed 56k. **whos2know you made my day**. :)

The .deb install worked and recompiled the driver for my kernel (2.6.xxx) automaticaly. You need to have a C compiler installed. It was on my release of Edubuntu (Feisty). The installer makes a link to */dev/modem* so the default configuration of the modem in Network connections worked just fine.

This one driver really was hard to find. Thx alot. I'll be watching the thread. Post if you need any assistance. Be glad to help.

Yves DL

---

### Post by m10 on 2007-10-16
i think the problem is that there (still) aren't **any** 56k modem drivers that work under 64 bit ubuntu (that i know of).

---

### Post by Linicks on 2007-10-16
Out of interest, check my post here:

[http://ubuntuforums.org/showthread.php?t=574233](http://ubuntuforums.org/showthread.php?t=574233)

Nick

---

