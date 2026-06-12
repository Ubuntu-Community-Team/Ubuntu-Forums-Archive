---
title: "Asus VX6-Pu17 Lamborghini problems"
date: 2011-01-24
forum: Hardware
---

### Post by icantthinkofausername on 2011-01-24
Does anyone else out there have one of these laptops? It runs that other operating system great but I am very much needing to get my portable Ubuntu fix.

First off I started looking at the netbook compatibility list. Which listed it as "Works great". Needless to say I am running into a bit of trouble :(.

- First I attempted the standard 10.10 i386 install. The install stopped and dropped me to a initramfs prompt.

- The second install attempt was with the i386 10.10 alternate. This did allow me to get the Ubuntu desktop installed. However when I installed the Broadcom STA wireless driver I got nothing but horrible wireless performance (somewhere around 90% packet loss when it would work). The wired Ethernet worked fine though. When I installed the Nvidia drivers and rebooted the system the desktop disappeared and returned me to a command line login. 

- I have since moved on to try the 11.04 alternate daily build....I am getting pretty much the same results as the 10.10 alternate. 


So who wrote the review on the netbook compatibly list? Any help from that individual or anyone else is greatly appreciated.

---

### Post by exelero on 2011-01-25
Hi,

I just got this netbook last week, I installed ubuntu 10.10 i386 desktop version without any problem, also I installed suggested wireless driver and it works fine. but I don't know why the name of this device is eth1!
 
But my ethernet device crash some times and I still have problem with microphone and headphone jack. 

Unfortunately, nvidia did't release the driver for linux ](*,) , as I know the problem is hybrid graphic card and optimus technology. I we have to configure xorg.conf and I don't know how.

I did't tried to configure other devices like multitouch pad or web cam.

---

### Post by icantthinkofausername on 2011-01-26
hmmm......a re-install of 10.10 alternate seems to have yielded good wifi results for me. 

For now I will probably leave the graphics alone unless anyone has suggestions for getting the Nvidia driver to work. I would really like to use the HDMI output. I don't think it will work without it.

---

### Post by grozni on 2011-01-27
> **icantthinkofausername said:**
> hmmm......a re-install of 10.10 alternate seems to have yielded good wifi results for me. 

For now I will probably leave the graphics alone unless anyone has suggestions for getting the Nvidia driver to work. I would really like to use the HDMI output. I don't think it will work without it.

I have same laptop. I was not able to install nvidia driver without issue. After nvidia install I always received shell login. The only thing I could find is how to disable nvidia graphic, but I didn't test it. I didn't find solution for optimus technology. I read that some bios on laptop have options to force nvidia as primary card. Unfortunately we don't have this option. Intel is always primary:(. I really hope that there will be solution for this issue with 2 graphic card. I want to use nvidia, I don't care about battery life and optimus technology. Mic isn't working, camera is working fine as well as everything else. If someone finds solution for mic, please sent solution.




Update 1 (MIC): I've played with audio settings for a while, trying to find solution for internal microphone. Asus VX6 has ALC269, I've tried as suggested:

adding line 

> options snd-hda-intel model=basic

to end of the file

> /etc/modprobe.d/alsa-base.conf


Reboot is necessary. After this microphone appear in alsamixer, it was muted. I've changed that and tried recording, not working:(. I've tried replacing model, instead of basic I've tried auto, fujitsu, lifebook. Everything that is described here for ALC269

[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt")

Nothing, absolutely nothing changed except MIC appeared in settings

---

### Post by grozni on 2011-02-04
I've finally made microphone working. The thing I did is to remove pulseaudio, and installing alsa. After this sound was not working at all, but after I added line 

> options snd-hda-intel model=auto

to

> /etc/modprobe.d/alsa-base.conf


everything was fine including microphone

---

### Post by sytchi on 2011-05-30
This modification led me to unexpected system crashes using 11.04 natty

---

