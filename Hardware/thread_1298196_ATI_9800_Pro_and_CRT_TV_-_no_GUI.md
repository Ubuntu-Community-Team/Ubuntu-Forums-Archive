---
title: "ATI 9800 Pro and CRT TV - no GUI"
date: 2009-10-22
forum: Hardware
---

### Post by dmanno on 2009-10-22
Hi all, 

First, I'd like to say that I'm still a Linux noob. I'm trying to learn but having difficulty on my HTPCish computer. 

I can not get any GUI to display when I connect my ATI Radeon 9800 Pro to my CRT HDTV. Ubuntu 9.04 will boot just fine, but I can not see anything when I connect to my CRT. I can ctl+alt+F3 etc. to bring up a terminal, but I can not get the desktop to appear. I can connect the computer to an LCD monitor and see everything just fine. I read there may be an issue with the 9800 pro and older cards, but I'm not sure since I CAN see the gui with a monitor.

I've searched and searched and tried this, that and the other but have not realized any results :(

I am not at home so I cannot post specific error messages, but when I try to get display properties, I receive a "Unable to open display" error. My xorg.conf file does not contain any info other than generic items like "Device" Identifier "Configured Video Device" but no options are listed, nor are any other items. I read that this file may not really be used anymore, so maybe this info is irrelevant...

Please help!

---

### Post by dmanno on 2009-10-22
Anyone have any ideas? I can't use Ubuntu on my livingroom computer if I just get a black screen when connected to the TV :(

---

### Post by dannon.37 on 2009-11-22
I'm in the exact same boat. Monitor works but tv doesn't. I'm almost certain it's a driver issue. I think what we need is a driver made for the radeon 9800 pro and not just the default ubuntu driver. From browsing around this forum though there's talk about there not being one anymore due to ati dropping support for older cards being used with linux. The Hardware Drivers menu doesn't show any drivers for it either (at least not in 9.10). If anyone has a driver or information on how to get the s-video to work with this card in 9.10 karmic koala please let us know. Thanks

ps. dmanno - This card works with a tv in intrepid ibex as there is a proprietary driver available, so even if this isn't solved we can just go back to that I suppose.

---

