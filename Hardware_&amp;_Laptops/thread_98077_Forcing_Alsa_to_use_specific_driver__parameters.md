---
title: "Forcing Alsa to use specific driver / parameters"
date: 2005-12-02
forum: Hardware &amp; Laptops
---

### Post by Mr. Swiveller on 2005-12-02
Hi there!

As you may have deduced from the subject title, I am trying to force Alsa to use a specific driver at boottime. 

The problem is that Alsa (correctly) identifies my soundcard as a Neomagic 256AV, and then loads the driver written for that card. This being a Thinkpad 390, however, the driver won't work. 

Due to modifications made by IBM, the driver that is required for 16-bit soundquality is snd_opl3sa2. The oss sb8-driver will also work, as I found out when I used Harddrake under an old Linux Mandrake install.

I am not sure how I should go about this on a (K)Ubuntu system. Is there an alsa.conf file I can edit? Or should I somehow modify the hotplug system? 

Any help is greatly appreciated!

Thanks in advance,

Swiveller

P.S. - I am using the Kubuntu version of Breezy.

---

### Post by Heretic09 on 2005-12-08
I guess you could blacklist the neomagic driver and then modprobe opl3sa2.

---

### Post by Mr. Swiveller on 2005-12-09
Thank you for the advice! 

I discovered that just running modprobe wouldn't do it, though. In order to get Breezy to accept the appropriate drivers, I had to run 

# modprobe --ignore-install snd-opl3sa2 port=0x120 dma1=0 dma2=1 irq=5 wss_port=0x530 fm_port=-1 midi_port=-1 isapnp=0

The 'ignore-install' command seemingly forces Alsa to accept whatever settings follow; the isapnp option tells Alsa this isn't a plug-and-play card.

Swiveller

---

