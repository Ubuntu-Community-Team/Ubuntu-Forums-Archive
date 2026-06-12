---
title: "Will Kubuntu Feisty detect and configure CRT display change?"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by mibadt on 2007-05-13
Hi,
My PC (Geoforce 6200+MAG 786PF CRT monitor) runs Kubuntu Feisty (7.0.4) without a problem (screen resolution 1024X768 @ 85 Hz). I'm considering buying the LG 1970HR (19" LCD) to replace my existing monitor and to be connected to the graphic card by DVI. 

My questions:
1. Will Kubuntu automatically detect the new hardware and reconfigure my X?
2. What are my options in case something goes wrong and the system won't boot graphically?
3. Has anybody experience with that specific LG model-I'd love to get tips and recommendations.

TIA

Michael Badt

---

### Post by aysiu on 2007-05-13
1. I believe you'll have to reconfigure X ```
sudo dpkg-reconfigure xserver-xorg
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal) should do it.

2. It will be able to boot graphically. You can always reconfigure the X server and make the settings more conservative (1024x768 instead of 1280x1024). Backing up the /etc/X11/xorg.conf file could help, too, so you can easily switch bak to your old monitor.

---

### Post by mibadt on 2007-05-14
Thanks a lot !

---

### Post by d-r-i-v-e on 2007-05-15
> **mibadt said:**
> Hi,
My PC (Geoforce 6200+MAG 786PF CRT monitor) runs Kubuntu Feisty (7.0.4) without a problem (screen resolution 1024X768 @ 85 Hz). I'm considering buying the LG 1970HR (19" LCD) to replace my existing monitor and to be connected to the graphic card by DVI. 

My questions:
1. Will Kubuntu automatically detect the new hardware and reconfigure my X?
2. What are my options in case something goes wrong and the system won't boot graphically?
3. Has anybody experience with that specific LG model-I'd love to get tips and recommendations.

TIA

Michael Badt

Hi!
I have almost the same configuration ( nVidia GeForce 6600 +MAG 786PF CRT monitor) but I cannot choose any frequency but the existing 60Hz. Do you have any idea  haw can I improve it up to 85 Hz?

Than you.

Daniel

---

