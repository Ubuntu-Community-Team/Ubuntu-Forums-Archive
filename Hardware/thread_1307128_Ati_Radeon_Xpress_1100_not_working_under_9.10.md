---
title: "Ati Radeon Xpress 1100 not working under 9.10"
date: 2009-10-30
forum: Hardware
---

### Post by Benjamin1987 on 2009-10-30
Hello,

My graphics cart is not working under Karmic Koala. When I first started Ubuntu after i installed 9.10 the wobbly windows were working, but after the next startup it wasn't working anymore. I installed all the components for compiz, but it still does not work, plz help!!

Thx

---

### Post by cer212 on 2009-11-15
I have the same problem for that video card, i have ubuntu 9,10 64 bits
i try to install the drivers for the xpress 200 but when is going to finish its showme this error :
[INDENT]**[FONT=Tahoma][COLOR=black]./default_policy.sh does not support version[/COLOR][/FONT]**
 [B][FONT=Tahoma][COLOR=black] default:v2:x86_64:lib32::none:2.6.31-14-generic; make sure that the version is being correctly set by --iscurrentdistro

Apology for my grammar xD
[/COLOR][/FONT][/B][/INDENT]

---

### Post by yoshiki2 on 2009-11-23
Open up a terminal and run the following commands

sudo apt-get install build-essential autoconf automake libtool pkg-config git-core

sudo apt-get install libdrm-dev x11proto-gl-dev mesa-common-dev xutils-dev x11proto-xf86dri-dev x11proto-fonts-dev x11proto-randr-dev x11proto-video-dev x11proto-xext-dev x11proto-xinerama-dev x11proto-render-dev xserver-xorg-dev

git clone git://[anongit.freedesktop.org/xorg/driver/xf86-video-ati]("http://anongit.freedesktop.org/xorg/driver/xf86-video-ati")

cd xf86-video-ati

sudo ./autogen.sh --prefix=/usr --enable-dri

sudo make

sudo make install

that used to work on 9.04.. no luck on 9.10..

---

### Post by Dinoyc on 2009-12-28
Hi All,

Even i am facing the same problem with my Acer 5100 series laptop where it has the below configuration

AMD turion 64 mobile technology
MK36 (2.0 Ghz,512k L2 cache)
15.4" widescreen WXGA wide Crystal brite TFT LCD
ATI Radeon Xpress 1100 Graphics Card
60GB PATA HDD
DVD-super Multi doule layer
(support DVD+R Doule Layer /DVD += RW)
512 MB RAM

I have installed Ubuntu 9.10 and i don't see any reason why we need to upgrade to 9.10 and degrade the kernel and XORG if that was the case then it would always be good to work on 8.10. I need to know if ubuntu is working with ATI to give us a legacy driver?
If yes then when is that day coming? is there a way we can mail the technical team of ubuntu to make them understand that issue?

Could someone suggest the best ATI graphics to upgrade to right now? which has a low budget and works in this configuration?

---

