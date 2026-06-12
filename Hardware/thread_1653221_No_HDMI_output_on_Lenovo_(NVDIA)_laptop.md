---
title: "No HDMI output on Lenovo (NVDIA) laptop"
date: 2010-12-26
forum: Hardware
---

### Post by mcdragon on 2010-12-26
Hi

I have been trying to connect my laptop to view films on my plasma TV using a brand new HDMI cable. My laptop is a Lenovo G550 with a nVidia graphic card GT218 (GeForce G210M) with Ubuntu 10.04 (lucid). My TV is LG 32PG6000.

Now I avoided installing the proprietary Nvidia driver as it screwed up my Ubuntu startup splash screen so I re-installed Ubuntu and did not install the drivers. I must also say I cannot use Compiz, I presume because I only have the basic linux video driver.

Has anybody had problems with HDMI on such a system? Do I have to install the nVidia drivers. I just don't want to screw-up the laptop (again).

bye
Martin
;)

---

### Post by lidex on 2010-12-26
I am not sure what video driver you need. This page has a good tutorial:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

---

### Post by mcdragon on 2010-12-28
Not sure myself. My card is listed in "Supported products" here: [http://www.nvidia.com/object/linux-display-ia32-260.19.29-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.29-driver.html)

I might just give it a try. I am just worried what its going to do to my laptop. I am not sure the problem is recoverable.

Thanks anyway lidex. :p

---

### Post by lidex on 2011-01-04
[http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22](http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22)

May be of help.

---

### Post by mcdragon on 2013-01-20
OK. Late update here but I think it was to do with the nouveau linux driver not being good enough.
I never bothered after that to fix the issue as using the laptop to watch films was not a necessity.

A couple of weeks ago I reinstalled the os to Ubuntu 12.10 and voila - problem fixed. By the way it also worked on Linux Mint 14 (Nadia) with the MATE desktop.
However I did actually have sevre problems when enabling the proprietary nVidia driver on Ubuntu 12.10 but as the nouveau driver worked fine I didn't bother with it.

P.S. I agree with Linus in giving nVidia the finger

---

