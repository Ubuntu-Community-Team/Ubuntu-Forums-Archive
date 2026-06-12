---
title: "Problem with HDMI connection"
date: 2018-11-09
forum: Hardware
---

### Post by penguinadventure on 2018-11-09
Hello.
I'm using Ubuntu 14.04. My laptop is an Acer Aspire 5738G, with a graphic card ATI Mobility Radeon HD4570.
From the first moment I installed Ubuntu everything has been working fine, including the graphics.
But now I cannot connect a new projector (LG PH30JG) using the HDMI connection.
It's the first time I'm trying to use HDMI in this laptop with Ubuntu.
In "System Settings"---"Displays" I can see the projector as "Goldstar Company Ltd. 72"". In the projector image something seems to happen with HDMI input, but after some seconds says "no signal".
I've been searching information about this problem, and seems to be related to the graphic card drivers. But in "Additional Drivers" I can't choose any other driver ("no additional drivers available"), although it says "not using proprietary drivers".
I've searched and downloaded the driver "amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64" from [www.amd.com](www.amd.com), but I don't know what to do with it, or if this will be the solution to my problem with HDMI.
I've had no problems with any driver or with the graphic card, so I'm not sure about changing drivers now.
Anybody can help me to connect the projector with HDMI?
Thank you.

---

### Post by penguinadventure on 2018-11-10
I've been messing around a little bit. The kernel driver installed in my laptop is RADEON, which I think is the open source driver (not proprietary driver).
Could be this driver unable to use my HDMI laptop connection? Would it work with another graphic card driver? I have downloaded this one from AMD:
amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64
But I don't know how to change drivers.

---

### Post by mitesh.agrwl on 2018-11-10
Hi,

Someone worked on it for good.

[Installation of AMD Drivers on Ubuntu and its Flavours]("https://forums.linuxmint.com/viewtopic.php?t=124012").

But before proceeding, have a backup and little insight of recovery if anything goes wrong.

Regards,
Mitesh

---

### Post by penguinadventure on 2018-11-10
Thank you Mitesh.

I've made a disaster trying to change the driver. Ubuntu has crashed....:(
I've decided to reinstall Ubuntu. Now I'm using version 18.04...:P
Once again, graphic card works perfectly from the first moment, with RADEON driver, and again HDMI connection is not working.
When I connect the projector the laptop seems to react for a second, and also something appears in the projector image, but after a few seconds nothing else happens, and HDMI doesn't works.

Instead of trying to change a driver that is working OK for everything else, I prefer to wait for someone who has experienced the same thing with the "Goldstar Company Ltd 72"".

---

### Post by mitesh.agrwl on 2018-11-10
Hi,

Sorry to hear that Ubuntu crashed. :( Had done myself a lot in early days, that is why I recommend to have a backup. 

Regarding HDMI issue, I am facing similar kind of problem with Samsung TV, 2010 model. The graphics card drivers are there but no image on TV with Lubuntu system. Do not have any Windows system to test but planning to borrow one for the purpose. TV manual instructs to use HDMI-1.3 port at peer end. I do not know how to check the specs of HDMI port or is it about the graphics card.

---

