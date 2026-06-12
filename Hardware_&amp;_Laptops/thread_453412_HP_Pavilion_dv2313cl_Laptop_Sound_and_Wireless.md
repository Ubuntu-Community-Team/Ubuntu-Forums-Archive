---
title: "HP Pavilion dv2313cl Laptop Sound and Wireless"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by fjgaude on 2007-05-24
Has anyone been able to get the subject laptop working under Feisty along with sound and WiFi?

frank

---

### Post by teaker1s on 2007-05-25
have a look at this, it's for the DV6000 but may provide useful tips
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29")

---

### Post by fjgaude on 2007-05-26
Thanks for the reply... I'm looking over the link... using Feisty the latest kernel already has the Broadcom drivers installed, the chipset used by HP dv2000 laptops; Dell also uses the same chipset. I do get the blue light saying the hardware has been turned on by the driver, bcm4311, and can see access points but cannot connect to any, roaming or WEP.

The sound issue is something else...

Thanks again for the help... one of these days Linux will have all these hardware issues solved, when it becomes more popular on the desktop. <smile>

frank

---

### Post by teaker1s on 2007-05-26
in which case use 
network-manager-gnome

---

### Post by lexarrow on 2007-05-27
for sound related issues check [this]("http://ubuntuforums.org/showthread.php?t=455147&highlight=dv2000") out.

---

### Post by syberdave on 2007-05-28
The kernel's broadcom drivers are broken. It turns on the blue LED okay, it detects access points okay, but it can't connect to anything. Use ndiswrapper.

---

### Post by fjgaude on 2007-05-29
> **teaker1s said:**
> in which case use 
network-manager-gnome

Tried everything with the wireless but nothing worked until, until the new kernel came in: 2.6.20-16. Then the Broadcom chip worked right off with me doing nothing. Connected to local access points at full speed.

Thanks to the crew who fixed it. Now to the sound, likely have to compiled ALSA after getting the source for the kernel.

frank

---

### Post by fjgaude on 2007-05-29
> **lexarrow said:**
> for sound related issues check [this]("http://ubuntuforums.org/showthread.php?t=455147&highlight=dv2000") out.

I'm going this route but can't seem to find the kernel source. Any ideas?

frank

---

### Post by syberdave on 2007-05-29
Strange. I just updated my kernel from 2.6.20.6 to 2.6.21.3 and the kernel wireless driver still doesn't work for me. However, sound is working better; previously, I had both a headphone and a speaker control. Now, it switches to whatever as I plug or unplug the headphones.

Just for the record, I have a Pavilion dv6253cL.
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

---

### Post by Niomi on 2007-06-19
Have you gotten your wireless driver working yet? I bought a HP Pavilion dv2313cl yesterday and got the wireless connection working today. The wireless card is a Broadcom 1390 which is also used in some dell laptops. The guide to installing this with ndiswrapper was written for dells, but it worked for me:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

I tried using ndiswrapper with HP drivers and that was a miserable failure.
For the convenience of searchers, I'll also post this in your other thread for these drivers.

---

