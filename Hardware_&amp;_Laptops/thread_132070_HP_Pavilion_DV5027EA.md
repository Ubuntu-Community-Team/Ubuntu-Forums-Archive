---
title: "HP Pavilion DV5027EA"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by darkwave on 2006-02-17
Ciao,

I'm thinking to buy a **HP Pavilion DV5027EA** with following specs (translated from the italian HP web site: [sito HP](http://h10010.www1.hp.com/wwpc/it/it/ho/WF06b/22655-186249-375899-375899-375899-12318232-68683569.html)):

**CPU**
	Mobile AMD Sempron™ 3300+ with PowerNow! (???), Cache L2 of 128 KB

**Memory**
	1024 MB
**Memory Type**
	DDR at 333 MHz
**Max Memory Supported**
	2 GB DDR
**Hard Disk**
	80 GB
**HD Controller**
	EIDE, ATA 100
**HD Speed**
	4200 rpm
**Optical Unit**
	DVD burner  (+/-R +/-RW) with Double Layer support

**Memory cards support**
	(6 in 1) (xD, SD, Smart Media, Memory Stick, Memory Stick Pro, Multimedia Card)
**modem**
	Modem 56K
**Ethernet**
	LAN Ethernet 10/100 integrata
**Wireless**
	WLAN 54g™ 802.11b/g
**I/O external ports**
	1 VGA port; 3 USB 2.0 ports; 1 IEEE-1394; RJ 11; Ethernet RJ 45; TV Out S-video; Irda

**Video Capture Interface**
	IEEE 1394 (Does it work under Ubuntu???)
**PCMCIA Slot**
	PC type I or type II. CardBus compatible. ExpressCard/54 (also ExpressCard/34)
**Display**
	WXGA da 15,4” High Definition BrightView Widescreen
**Screen resolution**
	1280 x 800
**Video RAM**
	128 MB dedicated
**Audio card**
	3D Sound Blaster Pro at 16 bit compatible[/quote]

Can you tell me if you see some components or reason to don't buy this laptop?

Somebody have experiences with a similar HP laptop? Some really bad issues?

Please, answer asap cause there is only 1 of this model in the shop (999euro...).

Thank you all in advance.

ciao,
dw

PS: I cannot find english documentation about this laptop... probably they sell it only in Italy...:-k

---

### Post by K.Mandla on 2006-02-17
It _*looks*_ okay, but I would want to know ...

- exactly what kind of wireless card is that?
- exactly what kind of video card is that?

If I were buying it, those would be the most important questions to me.

Maybe someone around here has a similar model. I tried to google this model, but all the pages were in Italian. :)

---

### Post by darkwave on 2006-02-17
[QUOTE=K.Mandla]It _*looks*_ okay, but I would want to know ...

- exactly what kind of wireless card is that?
- exactly what kind of video card is that?

If I were buying it, those would be the most important questions to me.

Maybe someone around here has a similar model. I tried to google this model, but all the pages were in Italian. :)[/QUOTE]
The video card is a ATI RADEON XPRESS 200M IGP.
Anyone had this card? Some know issues?

The Wi-Fi card should be a Broadcom 54g 802.11b/g wlan (I'm not sure...).

Anyway I already own a working PCMCIA wi-fi card that works with Ubuntu Breezy (Belkin F5D6020-V2).

Thank you.

dw

EDIT: I found [this link]("http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&product=1831917&jumpid=reg_R1002_USEN&cc=us&docname=c00603915") in english... doesn't say much more than what I translated here...

---

### Post by K.Mandla on 2006-02-18
Personally, I don't feel so good about it. The 200m cards are very picky. My brother has one, and I've seen [other posts]("http://ubuntuforums.org/showthread.php?t=132061") about it in this forum. You might want to search some more and see if it's possible to set it up right.

Similarly, the Broadcom wireless cards [can be tricky]("http://ubuntuforums.org/showthread.php?t=25683") to set up. I haven't worked with one myself, so it might not be terrible. But it's up to you if you think you want to get into it. Of course, you have the PCMCIA wireless to fall back on.

In my opinion, if it was me, and I wanted a laptop I was SURE would play nice with Ubuntu, I would probably look for another one. It's probably not fair for me to give advice one way or another, just because I haven't worked with one of those. But personally, I'd wait. E999 is a lot of money to pay and then be stuck with Windows. :-|

---

### Post by darkwave on 2006-02-18
Nooooo! I need a new laptop (my loved IBM Thinkpad A31 is going to die!!!).

**If someone has configured this video card please inform me!**

As I told the Wi-Fi is not a real problem for me and will not conditionate my choice.

ciao,
dw

---

### Post by darkwave on 2006-02-18
What about this?

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.22.5.html#172579](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.22.5.html#172579)

Somebody tried it?

ciao,
dw

---

### Post by Septor on 2006-02-20
The ATI driver works on Xpress 200 systems, but from what I understand you need to disable onbaord video memory and only use system RAM for video.  Once you do this, the driver works fine for most people.

---

### Post by darkwave on 2006-02-21
I installed the [latest ATI drivers]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27") and everything works fine. I didn't tested 3D acceleration but the screen looks fantastic in KDE/Gnome :)

Remember: you have to install kernel source and other building packages in order to install ATI drivers. There are installation instructions in [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.20.x_drivers_in_Breezy_Badger").

Ciao,
dw

PS: The HP Pavilion dv5027ea works with Ubuntu. Only the wi-fi is not detected. I didn't tried ndiswrapper...

---

### Post by gregh on 2006-06-26
I have a HP Pavillion dv5000 and mainly works out the box.
The inbuilt sd card reader does not work, (but a usb multi-reader does) and suspend/hibernate is a bit dodgy, but apart from that I am very happy (it uses a nvidia 6400 go for video) I purposly looked for a laptop *without* ati chipset due to teh problems with the lack of support for them

-Greg

---

