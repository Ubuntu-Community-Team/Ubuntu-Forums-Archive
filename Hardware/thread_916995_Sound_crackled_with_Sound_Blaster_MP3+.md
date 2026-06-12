---
title: "Sound crackled with Sound Blaster MP3+"
date: 2008-09-11
forum: Hardware
---

### Post by Asuriel on 2008-09-11
Hi at all. 

I installed ubuntu 8.04 in my desktop last month. All worked properly except my USB Sound Blaster Mp3+ that was installed properly but played a crackled sound either mp3 and wav (aplay tool). The problem wasn't in volume controls, because I modified one to one all alsamixer setting without results. 
I worked on a lot without results.
Serendipity when I've plugged Sound Blaster MP3 directly to **computer USB** It has worked well !
So the problem is simply: don't plug USB Sound Blaster MP3+ via USB HUB !!!

Regards. :)

Asuriel

---

### Post by ciarz3r on 2008-12-28
I'm using Kubuntu 8.10 and I can't get my sound to work with the USB creative sound blaster mp3+. When I directly insert the USB cable I hear a crackle but no sound when I try and play an mp3 or watch a video on youtube. I can hear sound using headphones though. I haven't installed the sound card at all. Can't find a driver for (k)ubuntu. How did you install it properly. I've just plugged it in and hoped for the best like.

'cat /proc/asound/cards' outputs:
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981A at irq 17
 2 [MP3            ]: USB-Audio - Sound Blaster MP3+
                      Creative Labs Sound Blaster MP3+ at usb-0000:00:1d.1-1, full speed

I think I've already installed the alsa drivers using:
'sudo apt-get install alsa-oss'

Sometimes when I'm logging off I hear like 1 second of the "log off music".

---

