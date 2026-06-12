---
title: "Nb asus f6a-3p044c"
date: 2008-09-09
forum: Hardware
---

### Post by fisk on 2008-09-09
Hi! ;)

Does anyone of you have experience running Ubuntu Hardy on this laptop:
ASUS F6A-3P044C ?

Do you know if everything is ok?
Are there known problems (wifi, video, compiz.. )?

Some details here:

Mobile Intel Centrino DUO Technology 
Intel Core2 Duo T5750 2.0Ghz (667MHz FSB; 2MB on die L2 Cache) 
Chipset Mobile Intel GM45 Express Chipset +ICH9M 
Mem: 3GB DDR2 800Mhz 
Display TFT 13.3" WXGA Glare Color-Shine 
Video: Intel GMA X4500HD (GM45) 
Hard Disk 250GB SATA 5400 
DVD Super Multi DUAL Layer 
Bluetooth V2.0+EDR 
Gigabit LAN 10/100/1000 Mbps 
Wireless LAN 802.11a/g/n 
Webcam 1.3 MPx
8 in 1 card reader
TPM e Fingerprint 

Thank you!
Bye :)

---

### Post by fisk on 2008-09-10
No one knows about issues?

Do you think the hardware is ok?

I've read something about the video card here:
[http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=1)
and it seems ok.

But I don't know about the chipset, the wifi, the fan...etc

Any suggestion?

---

### Post by Mr.Carramba on 2008-09-10
some have to be first :) why not you? :D

---

### Post by Nite2006 on 2008-11-08
Latest kubuntu (2.6.27-7-generic) on this ntb works perfectly
Video ok
```
direct rendering: Yes  
server glx vendor string: SGI
server glx version string: 1.2

```
Lan ok
Wifi ok
Camera ok
Touchpad ok
hdmi ok
Acpi (suspend etc) ok
Fingerprint no 

but i've some problem with sound config

---

### Post by mecat on 2008-11-17
i tried many parametrs (in alsa-base) with audio realtec 622 rev1 codecs with no success. can you help me and send your configs?

best regard

---

### Post by mecat on 2008-11-17
i made it. you need to update your distro and add to /etc/modprobe.d/alsa-base
options snd-hda-intel model=eeepc-ep20

best regards

---

