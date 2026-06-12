---
title: "Samsung X20 Soundcard problems"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by leozilla on 2005-05-17
Hello everybody!

I have problems with my soundcard under the 2.6.11-6 kernel.
Bevor I was using kubuntu-5.04 with 2.6.10 kernel and with this kernel the sound works out great.

My Hardware, i have a Samsung X20 Notebook und here's my lspci output:

leo@X20:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
**0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)**
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:06:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:06:07.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:06:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:06:09.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
0000:06:09.2 0805: Ricoh Co Ltd: Unknown device 0822 (rev 17)
0000:06:09.3 System peripheral: Ricoh Co Ltd: Unknown device 0592 (rev 08)

I have tried the driver's built-in and as modules, i am sure those are the right drivers:

leo@X20:~$ lsmod
Module                  Size  Used by
af_packet              18312  2
ipw2200                161096  0
ieee80211             41316  1 ipw2200
ieee80211_crypt   6088  2 ipw2200,ieee80211
b44                        23108  0
snd_intel8x0          33664  1
snd_ac97_codec   78712  1 snd_intel8x0
snd_pcm_oss         54048  0
snd_mixer_oss        20352  2 snd_pcm_oss
snd_pcm                95560  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25988  1 snd_pcm
snd                        55524  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc     10116  2 snd_intel8x0,snd_pcm
..

I used this kernel configuration: [http://pathfinderteam.org/debian/sx20/kernel-2.6.11.6.conf](http://pathfinderteam.org/debian/sx20/kernel-2.6.11.6.conf)
from this page: [http://faq.pathfinderteam.org/index.php/Samsung_X20](http://faq.pathfinderteam.org/index.php/Samsung_X20)

I really dont know what to do, because the modules are loaded and alsamixer works, but theres no sound anyway

pls help  :|

---

### Post by CLod on 2006-12-05
mi pare ci sia ancora aperto un bug su alsa per questo problema con questa     sheda
anche io ho lo stesso problema

---

