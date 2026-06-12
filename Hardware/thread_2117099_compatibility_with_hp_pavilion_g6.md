---
title: "compatibility with hp pavilion g6"
date: 2013-02-17
forum: Hardware
---

### Post by andreuec on 2013-02-17
I checked the official compatible laptop list and I didn't see mine, but there was the g4 and the g7 so I want to know if I can get Ubuntu (12.10 or 12.04 I guess?) running in my laptop, and I thought posting in the ubuntu forums. Could you help me, please? :)

There goes some info from my dxdiag:

Time of this report: 2/17/2013, 20:05:32
Operating System: Windows 8 64-bit (6.2, Build 9200) (9200.win8_rtm.120725-1247)
System Manufacturer: Hewlett-Packard
System Model: HP Pavilion g6 Notebook PC
BIOS: F.15
Processor: AMD A6-4400M APU with Radeon(tm) HD Graphics    (2 CPUs), ~2.7GHz
Memory: 4096MB RAM
Available OS Memory: 3554MB RAM
Page File: 2363MB used, 1830MB available
DirectX Version: DirectX 11
DxDiag Version: 6.02.9200.16384 64bit Unicode

Thanks in advance :D

---

### Post by sulekhadahiya on 2013-02-17
I have HP g6-2313AX notebook. I have Ubuntu on it and I have to install drivers for graphics from AMD site and wifi/blutooth not working. see this thread [http://ubuntuforums.org/showthread.php?t=2116856]("http://ubuntuforums.org/showthread.php?t=2116856")

---

### Post by sulekhadahiya on 2013-02-17
> **andreuec said:**
> I checked the official compatible laptop list and I didn't see mine, but there was the g4 and the g7 so I want to know if I can get Ubuntu (12.10 or 12.04 I guess?) running in my laptop, and I thought posting in the ubuntu forums. Could you help me, please? :)



You check your g6 series notebook details [from HP website with this link]("http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=us&taskId=135&prodClassId=-1&prodTypeId=321957&prodSeriesId=5330578") or [here]("http://blog.icewheel.org/2013/02/hp-pavilion-g6-2313ax-drivers.html")

---

### Post by andreuec on 2013-02-18
wow thanks for answering so fast :), I'll see which model is mine and try to understand if it would work with Ubuntu as soon as I can.
It'd be a pity if the wifi doesn't work, but if that were to be the case, maybe I could install an older version or something?
Anyway, thanks a lot for the info, I really appreciate it! ^^

---

### Post by albandy on 2013-02-18
Try it in livecd mode. If works the only thing you've to worry about is installing the ati drivers, but usually are detected automatically and the system will ask you to install it.

---

### Post by andreuec on 2013-02-25
I got the model, it's a Hewlett Packard Pavilion g6-2254ss ([http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c03559258](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c03559258)).

I wanted to try the Live CD mode, as **albandy **kindly suggested, before installing so I asked a friend who has Ubuntu to help me and he prepared me an Ubuntu 12.10 32bit version LiveUSB, but I've been searching and it seems my computer could need the 64bit version as it runs Windows 8 and comes with the UEFI thing... ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)).

I'm downloading the Ubuntu-Secure-Remix-12.10-64bit iso right now as the UEFI page (link above) suggests, but it will take some time.
I also have some DVDs around (I'd rather not delete the LiveUSB, just in case...).

It seems quite obvious to me that I should follow the steps described in the mentioned page, but as I am a complete noob in this matter, could anyone confirm or deny it?

Thanks :D
And thanks to everyone who replied my older posts too :D

---

### Post by SimonDPRZ on 2013-02-25
32bit will work on your 64 bit pc but you can use 64 bit version. 

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
use this it is very easy to create a liveUSB. instal program en follow directions

---

### Post by andreuec on 2013-02-26
Thanks to all of you, I finally got to try the 12.10 64bit version in LiveUSB mode (it seems LiveCD won't work for some computers with UEFI BIOS: [http://ubuntuforums.org/showthread.php?p=12530420](http://ubuntuforums.org/showthread.php?p=12530420)).

I have the same problems as **khatkarrohit **now, at least the ones concerning the wireless:

[QUOTE=khatkarrohit]**Wireless Connectivity:Bluetooth, 802.11b/g/n**
Neither wireless nor Bluetooth works with ubuntu. Wireless works with  Ralink RT3290 firmware but only with upgraded Linux kernel to 3.7.8.  Even after few minutes wifi stopped working and it says device not  ready. Bluetooth never worked.[/QUOTE]

So I guess I'll just have to wait as well :(

[QUOTE=khatkarrohit]Waiting for the new release of Ubuntu 13.04 otherwise have to switch  back to windows for this laptop to work for me. I read on a website that  Ubuntu 13.04 has new kernel 3.7.8, which support brightness control and  wifi and maybe other things too.[/QUOTE]

I have yet to check the other issues he reported, but it seems I'll have to install the graphics drivers too and maybe fix some other things.

---

