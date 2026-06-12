---
title: "Radeon HD4200 series (and other) issues"
date: 2013-04-14
forum: Hardware
---

### Post by CoximusPrime on 2013-04-14
Hi guys,

At the moment I have a rather large paper weight in the form of a HP N40L ([http://h18004.www1.hp.com/products/q.../13716_na.HTML](http://h18004.www1.hp.com/products/q.../13716_na.HTML)) which I want to run XBMC.

This has an onboard ATI Readon HD 4200 series graphics card, of which I have to use the VGA port (as the TV I'm connecting it to does not have HDMI).

Since I am using the VGA port and it N40L has no onboard audio, I purchased a PCIe Asus Xonar DGX, which has a CMI8788 chipset.

If I go with the latest version of ubuntu 12.04 or 12.10, the audio is supported as it is running a kernel version of 3.5 or greater (which [http://askubuntu.com/questions/19246...set-sound-card](http://askubuntu.com/questions/19246...set-sound-card) says is needed for alsa audio with this card), but and amd/ati legacy drivers do not work for the onboard graphics.

If I go with the latest linux mint (and do not update the kernel) onboard graphics works fine, but the alsa audio drivers are not supported.

I have tried the makson96/fglrx repository to install the legacy drivers in ubuntu, but this results in unity not showing (so I just get my background image and the ability to right click and get some settings), and XBMC fails to load due to OpenGL errors.

Does anybody have any suggestions about which would be easier, getting the graphics to work in later kernel versions, or getting audio to work in earlier versions .... and can anybody tell me how to do it?? It has been driving me insane for about 3 weeks now.

Thanks everyone.

---

### Post by Mark Phelps on 2013-04-16
From what I've read on the forum, to get your graphics chip to work with 12.04.2, 12.10, 13.04, or newer, you have to run some utility which forces an older X-server installation -- which is only going to lead to more problems down the road, even though it works today.

Have you checked to see if there are OSS drivers that work with that audio chipset?  I know that they work with many CMI chipsets, just don't know if they work with that one.  If that works, you will need to stick with an earlier Ubuntu version, but you'll get working audio as well as video.

---

