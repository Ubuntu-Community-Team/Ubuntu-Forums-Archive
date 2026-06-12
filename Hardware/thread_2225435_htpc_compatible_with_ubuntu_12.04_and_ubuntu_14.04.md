---
title: "htpc compatible with ubuntu 12.04 and ubuntu 14.04"
date: 2014-05-21
forum: Hardware
---

### Post by ckrles on 2014-05-21
Hello everybody. Before I make any questions, I would like to thank all the community that helps some many people just arrived to linux as myself. I'm quite of a noob. I've been using ubuntu-based distros such as Zorin 6 and mint for a year and a half. Here is my question/problem.

I'm building a low profile pc (let's call htpc) for my wife's business. She won't be needing too much power and she wants the device not to be too big, so that's why we chose to build a mini-itx motherboard-based system. We will be connecting it to an external monitor. The problem is that I don't find any suitable motherboard that is compatible and not having any issues with graphics. I had taken a look at asrock ad2550-itx, but there is a major problem, which is that it has built-in cpu (intel atom d2550) with powerVR graphics (SGX545 or gm3600 chipset). So, as you all know there is no driver available for the graphics card on linux. Such a shame because in terms of cpu, power use and heat it was quite a good choice (just my opinion).

So..... would you please recommend me a mini-itx moherboard which has buil-in cpu and graphic card which is compatible? Since heat is a concern in mini-itx boxes I would really appreciate it to have a low power use. Not sure but I think amd systems heat up a little bit more than intel ones.

I've really have no idea on what to choose. What about motherboard [SIZE=2]Gigabyte GA-C1037UN-EU[/SIZE] with integrated cpu Intel® Dual-core Celeron® 1037U processor (1.8 GHz)?

I have another doubt. In terms of screen resolution, what would happen if I buy the asrock ad2550-itx with atom d2550? Anyone having thos cpu or motherboard. I have read a lot of threads and different people have different resolutions. I've rad that ubuntu runs worse than Windows because of the lack of graphic card driver. I think HDMI doesn't work. I'm not going to watch hd movies, but you never know when you're gonna need to. I intend to install ubuntu 12.04 (quite possibly zorin 6) or ubuntu 14.04.

I've read a lot of threads hoping to find a solution but it seems that there isn't. Do you know if the problem with the graphics card is solved in ubuntu 14.04? (wishful thinking :D:D:D)

I'd really appreciate some help. My wife is putting pressure on me ;-);-);-) She wants it asap because she needs it, and she says she'll "borrowing my laptop" permanently until she gets her system.

Thank you all very much in advanced.

---

### Post by oldfred on 2014-05-21
I have been thinking of building a similar system and added these links to my notes.

[http://www.phoronix.com/scan.php?page=article&item=silverstone_milo_ml06&num=3](http://www.phoronix.com/scan.php?page=article&item=silverstone_milo_ml06&num=3)
[http://www.phoronix.com/scan.php?page=article&item=silverstone_raven_rvz01&num=1](http://www.phoronix.com/scan.php?page=article&item=silverstone_raven_rvz01&num=1)
[http://www.phoronix.com/scan.php?page=article&item=rosewill_mini_itx&num=3](http://www.phoronix.com/scan.php?page=article&item=rosewill_mini_itx&num=3)

SilverStone SG05-LITE: Building A Low-Cost, Linux, Mini-ITX System
[http://www.phoronix.com/scan.php?page=article&item=mini_itx_linux2014&num=1](http://www.phoronix.com/scan.php?page=article&item=mini_itx_linux2014&num=1)
Corsair CX430: A Decent Low-Cost Power Supply
[http://www.phoronix.com/scan.php?page=article&item=corsair_cx430_psu&num=1](http://www.phoronix.com/scan.php?page=article&item=corsair_cx430_psu&num=1)

 Intel NUC
[http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html](http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html)
[http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html](http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html)
[http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1)
UEFI - in efi partition Manual copy grubx64.efi to bootx64.efi to make it work.
[http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/)
BIOS update fixes some issues
[http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/](http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/)

I would prefer to build my own system but use Intel chips.

---

### Post by markosjal on 2014-05-22
I wanted to share a great find here. This is much smaller than Mini ITX, in fact similar to NUC but maybe smaller still?? I bought one of these and was impressed with the HD2000 Performance with the standard 2 GB RAM and 8GB SSD

The only problem I have is that I can not get the info for how to configre the ITE 8704 CIR header to work with Linux. I tested with an install of Win and MCE and the sony MCE remote worked beautifully with WMC and the IR Sensor (Vishay TSOP38238) that I added "out of the box" . No power on from remote however as I can see ther power is killed to the CIR header when turned off and the only available power when turned off would be from a rear USB port

I have tested multiple HD 1080p videos on XBMC and it is darn impressive 

It even will mount on rear of small monitor with included mounting bracket. If you want to install a hard disk you need the optional bottom plate Hard disk housing.
[http://www.aliexpress.com/item/Super-Mini-PC-X3700m-Intel-Celeron-1037u-Dual-Core-1-8Ghz-Processor-2GB-RAM-8GB-SSD/1593071054.html](http://www.aliexpress.com/item/Super-Mini-PC-X3700m-Intel-Celeron-1037u-Dual-Core-1-8Ghz-Processor-2GB-RAM-8GB-SSD/1593071054.html)


I now have one of these on the way:
[http://www.aliexpress.com/item/linux-micro-pc-mainframe-computer-thin-computing-L-19X-E3501-6G-HZ-2G-RAM-8G-SSD/1625482917.html](http://www.aliexpress.com/item/linux-micro-pc-mainframe-computer-thin-computing-L-19X-E3501-6G-HZ-2G-RAM-8G-SSD/1625482917.html)

I figure it will be a step down from the previous one, and slightly larger,  but probably will do HD and load xbmc menus just fine

---

### Post by ckrles on 2014-05-22
I've had a look at what you've posted, but I'd like a motherboard with integrated cpu and integrated graphics card. I don't need it to be very powerful, just powerful enough to run ubuntu 14.04lts smoothly and I want to avoid heat issues. Any suggestions? And I'd prefer to buy it a at local shop. The point is I had already ordered asrock ad2550-itx at my local shop and then I noticed the driver issues. Since I have to give it back to the shop and it causes them some trouble I'd like to buy the equipment from them. Right know I've the asrock ad2550-itx at home prepared and I'm gonna trying installing different ubuntu versions.

Thank you.

---

### Post by ckrles on 2014-05-23
What do you think about these two mobos?
GIGABYTE GA-J1800N-D2H (GA-C1037UN-EU
GIGABYTE GA-C1037UN-EU

Are they compatible with linux and ubuntu? Any compatibility issues of their cpu and graphics card? Are they powerful enough to run ubuntu 12.04 and ubuntu 14.04?

I would really appreciate opinions and comments from people who have them running ubuntu.

Thank you very much.

---

### Post by oldfred on 2014-05-23
Are the internals the same as this?
[http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=5](http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=5)

---

### Post by ckrles on 2014-05-23
I'm quite of a noob and I don't fully understand the info in the link.

What do you think of these mini-itx mobos?

[h=1][SIZE=1]ASUS J1800I-A intel celeron Intel® Celeron® Prozessor J1800  Intel Hd graphics[/SIZE][/h][SIZE=1]
[/SIZE][h=1][SIZE=1]GIGABYTE GA-J1800N-D2H (rev. 1.0) Intel Celeron J1800
[/SIZE][/h][SIZE=1]
[/SIZE][h=1][SIZE=1]GIGABYTE GA-C1037UN-EU Intel Celeron 1037u Chipset NM70 Express
[/SIZE][/h][SIZE=1]                       [/SIZE][h=1][SIZE=1]GIGABYTE GA-J1900N-D3V (rev. 1.0)[/SIZE][/h]All of them have Intel HD graphics. Is there any compatibility problem?

So, I would like to know which one would you choose keeping in mind compatibility and trying to keep heat under control.

I got all the info from [http://www.alternate.es/html/listings/Hardware-Componentes-Placas-base-Intel-CPU-integrada/621?tk=7&lk=6770](http://www.alternate.es/html/listings/Hardware-Componentes-Placas-base-Intel-CPU-integrada/621?tk=7&lk=6770) in case you could have a look for further info.

Recommendations and comments are most welcome.
Thank you very much.

---

