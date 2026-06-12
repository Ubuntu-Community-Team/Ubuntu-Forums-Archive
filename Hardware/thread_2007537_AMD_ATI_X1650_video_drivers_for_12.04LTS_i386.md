---
title: "AMD ATI X1650 video drivers for 12.04LTS i386"
date: 2012-06-20
forum: Hardware
---

### Post by Windwalker52 on 2012-06-20
I am using a AMD ATI X1650 graphics card on 12.04 i386 with a AMD 1.6GHz dual core CPU and I don't know how to install advanced drivers to take advantage of a secondhand video card. Is there a better forum or a method a newbie can understand?
:popcorn:

---

### Post by pme 72 on 2012-06-23
From my understanding the situation for the ATI X-series cards is basically unchanged since before Lucid. The default Radeon driver is what is available. The AMD provided Legacy driver will not work with Linux kernels newer that about 2009. I searched the forums for "ATI X1650" and found a lot of posts but none are particularly optimistic. I switched out my X1550 in Lucid when some of the tracks in SuperTuxKart experienced rendering issues. 

You can try Ask Ubuntu:
[http://askubuntu.com/](http://askubuntu.com/)


Here is the official Precise Installation Guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#)

> Which cards are no longer supported by ATI? The ATI Radeon 9500-9800, Xpress200-1250, 690G, 740G, [COLOR="Red"]X300-X2500[/COLOR] (including Mobility RadeonHD 2300, since it is really a DirectX 9 part). See the complete list here. If your card is on that list, you are limited to open-source drivers on Ubuntu Lucid/10.04 (and later). If you really need the proprietary Catalyst/fglrx driver, you will have to use an older Linux distribution, such as Debian Lenny/5.0.x or Ubuntu Hardy/8.04.x. 

---

