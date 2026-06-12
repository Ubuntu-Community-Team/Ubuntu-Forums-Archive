---
title: "Radeon 9600 Mobility + ATI Proprietary Driver (xorg-driver-fglrx) + Hardy v8.04.2?"
date: 2009-06-06
forum: Hardware
---

### Post by allbread on 2009-06-06
I just installed Ubuntu Hardy v8.04.2 (32 bit) on my laptop last night and would like to know if it is wise to install the proprietary ATI drivers (xorg-driver-fglrx) via the Synaptic Package Manager...

Prior to the install I read about issues with the proprietary drivers with older ATI GPUs (my laptop runs a Mobility 9600 - RV350 core) but I'm not sure what the current status is. I would like to do a bit of dual monitor spanning (via a docking station port extender) that I have and I gather this can only really be done under the ATI drivers... however at present the open source drivers seem to be working fine and I'm worried I might hose my system if I install fault display drivers.[B]

What is the current status of these drivers... should I take the plunge and install?[/B]

---

### Post by Legace on 2009-06-06
> **allbread said:**
> What is the current status of these drivers... should I take the plunge and install?[/B]

If the open-source drivers are working for you, then I'd stick with them.
The FGLRX drivers have probles (video playback with Compiz enabled doesn't work, for example).

But, if you find the courage to install FGLRX, you have to install the 9.3 (or lower) version as version 9.4 dropped support for your card :)

Here is a nice guide: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method)

---

### Post by allbread on 2009-06-06
Legace: Thanks for the info!

Do you know if monitor spanning is supported under the open source drivers?

Is hardware acceleration *only* supported under the proprietary drivers?

In Synaptic I see the ati-driver-fglrx version as 1:7.1.0-8-3+2.6.24.... is there a later version of this driver (that still supports my Radeon Mobility 9600) that fixes the video playback / Compiz issues you described above?

I remember reading on a forum (phoronix perhaps?) that in some instances, for older hardware such as my own, the older drivers were better but were only supported under Hardy. This is one of the reasons I decided to install Hardy as opposed to one of the newer releases...

If there is a new version of the driver than the one supported in Synaptic should I take a shot at installing it via the "Manual" method described in the link you posted... aside from overall performance what are the pros/cons of proprietary vs open-source drivers in this particular instance?

(sorry for the long winded edit... hoping you decided to take just one more look at this thread:)

---

### Post by Legace on 2009-06-06
The open source drivers should be more than enough for you, as they support 3D acceleration and composting (Compiz should work :)).
-> [https://help.ubuntu.com/community/RadeonDriver#Accelerated%203D%20support%20(r300,%20r400%20and%20r500%20series](https://help.ubuntu.com/community/RadeonDriver#Accelerated%203D%20support%20(r300,%20r400%20and%20r500%20series)

I don't know monitor spanning works though.

---

