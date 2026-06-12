---
title: "Dell D630 Wirless problems on Ubuntu 10.04 and 10.10"
date: 2010-10-01
forum: Hardware
---

### Post by ninja001 on 2010-10-01
I have installed Ubuntu 10.04 on my Dell D630 laptop with a wireless card (Intel 4965 AGN and Broadcom Ethernet Controller BCM5755M)

After installing Ubuntu Netbook Remix 10.04 I always had my wireless light blinking and while browsing the internet, it would stop and I would have to refresh the page in order for it work. I have a dual boot windows 7 and Ubuntu 10.04. I am a novice Ubuntu user and I don't work my way around too well in terminal. I have used browsed a lot in Windows and I have never encountered this issue. Neither thus the wireless light blink. It remains solid when it's on.

I have tried using an ethernet cable as well and I had the same issue with the web browsing in ubuntu. The browser would simply stop loading the page and I would have to reload the page and continue surfing. This happens quite frequently and it's annoying. 

I have googled around solutions but I have not managed to successfully install the driver. In fact I now don't have wireless internet, only the ethernet cable works. 

I have used the following instructions to fix the issue, but to no avail: 

[http://kuscsik.blogspot.com/search?q=wireless+ubuntu](http://kuscsik.blogspot.com/search?q=wireless+ubuntu)

I have looked into installing the ndiswrapper solution but I am not sure what driver's to download. 

I have installed Ubuntu 10.10 beta candidate hoping this would solve the problem but it has not. The problem has persisted. I hope that someone will be able to help me because I would love to continue working on Ubuntu and support open source software.

---

### Post by Phkillah on 2010-10-07
I'm using RC as well and i've lost ethernet link with BCM5755M also....

---

### Post by Carl.Spackler on 2010-10-08
To help with the blinking if you want.
 
The blinking LED on the Intel card is a part of the driver firmware. I have a script that I put together with credit from other sources after researching this issue and it worked for my Intel 4965, Intel 5100 and Intel 5300 cards that I had in my Dell D630. Download the attachment below, open and save the files to a temporary directory inside you home or work directory. There are two files. The one called "noflashled" is the actual file that changes the LED parameters on boot of the machine. The other file is the installation script. It will put the noflashled file where it needs to be and change the permissions so it gets executed during boot.
 
Let me know if this helps!

---

