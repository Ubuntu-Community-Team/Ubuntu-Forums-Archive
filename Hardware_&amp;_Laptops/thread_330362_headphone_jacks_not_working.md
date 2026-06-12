---
title: "headphone jacks not working"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by Unreallinux on 2007-01-03
Can someone help me fix the audio jacks on my laptop? I have this laptop:
[http://www.circuitcity.com/ssm/Toshiba-Satellite-15-4-Widescreen-Notebook-PC-L35-S2161/sem/rpsm/oid/165319/catOid/-12963/rpem/ccd/productDetail.do](http://www.circuitcity.com/ssm/Toshiba-Satellite-15-4-Widescreen-Notebook-PC-L35-S2161/sem/rpsm/oid/165319/catOid/-12963/rpem/ccd/productDetail.do)

I would provide info but I'm not sure what will help. :(
This is the last step before I can dump windows on this pc for good!

I'm pretty impressed with what I've done today.
I've managed to get WPA and my Video card to work!(the dreaded radeon express 200m)

---

### Post by eggdeng on 2007-01-03
Can you post the output of```
lspci
``` to see if it identifies your soundcard. Also ```
cat /proc/asound/version
cat /proc/asound/cards
cat /proc/asound/modules

``` for information about the alsa driver.

---

### Post by Pjotr123 on 2007-01-03
Install alsamixergui for a complete graphical control of your sound card. You can use Synaptic for that, alsamixergui is in the standard Ubuntu repositories.

Greeting, Pjotr.

---

### Post by Unreallinux on 2007-01-03
Thanks for helping guys. I already had that program installed. :(

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a31 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
0000:00:14.2 0403: ATI Technologies Inc: Unknown device 437b (rev 01)
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a62
0000:09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:09:04.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
---------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
---------------------------
0 [SB             ]: HDA-Intel - HDA ATI SB
                     HDA ATI SB at 0xd0400000 irq 201
-------------------------
0 snd_hda_intel

I ran those commands in the same order you posted them.

---

### Post by nkassi on 2007-01-03
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

This should help you out to install the newest Alsa drivers. I had the same issue. It's not quite perfect (it woun't shut off you speakers when you plug in you headphones) but it works.

Nic

---

### Post by eggdeng on 2007-01-03
I can't see any soundcard in the lspci output but alsa seems to think it's Intel HDA. It may not be necessary to update your alsa driver as the version you have should be OK, although it's probably no harm. 
The crucial point is what line to add at the end of /etc/modprobe.d/alsa-base, it will be something along the lines of 
```
options snd-hda-intel model= dell
```
See this thread for more information. [http://www.ubuntuforums.org/showthread.php?t=314383](http://www.ubuntuforums.org/showthread.php?t=314383)

---

