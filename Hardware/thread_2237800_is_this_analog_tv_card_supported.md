---
title: "is this analog tv card supported?"
date: 2014-08-04
forum: Hardware
---

### Post by nargaroth_reg on 2014-08-04
Hello, I have this [http://www.mygica.com/old/pa/top103fm.asp](http://www.mygica.com/old/pa/top103fm.asp) analog tv card and I'd like to know if there's a linux driver for it.
Thanks!

---

### Post by Bucky Ball on 2014-08-04
*Thread moved to **Multimedia**.*

Welcome. Boot the computer with the stick out. Plug it in once at a stable desktop, then, before doing anything else, immediately open a terminal and issue:

```
dmesg
```

At the bottom of the output should be details of what you've just plugged in. Please post the relevant information here, along with the output of this, with the device plugged in:

```
lsusb
```

Please use [code] tags around the output when posting. [ /code] Thanks.

PS: Have you tried plugging it in and trying it? It may just work. Many do. It depends on the card/chip inside the device rather than the device itself (the TV dongle's brand name/model, etc.). That is what you may be looking for the drivers for.

---

### Post by nargaroth_reg on 2014-08-04
Hey, thanks for your reply. It is a PCI card, here are the details provided by lspci 
```
Slot:    03:05.0
Class:    Multimedia controller
Vendor:    Philips Semiconductors
Device:    SAA7130 Video Broadcast Decoder
SVendor:    Philips Semiconductors
SDevice:    SAA7130-based TV tuner card
Rev:    01
```

PS I could not use it in a live session with tvtime (the program was not recognizing the card).

---

### Post by Bucky Ball on 2014-08-04
... and the result from dmesg after plugging it in, thanks.

---

### Post by coffeecat on 2014-08-04
*Thread moved to **Hardware**.*

---

### Post by nargaroth_reg on 2014-08-05
I can't unplug it since it's a PCI card... also I can't do a complete install right now, just test it with the latest lts live session, do you think the info from dmesg will be usable anyway?
From what I've read here [https://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux](https://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux) it looks like it depends much on luck and patience to try the different card numbers.

---

### Post by nargaroth_reg on 2014-08-15
With a bit of luck and patience I got it working, I leave some of the information I found here in case someone else has this same type of card.
To get the video working basically: 
sudo rmmod saa7134_dvb saa7134_alsa saa7134
sudo modprobe saa7134 card=**184**  
I didn't need to set the tuner number or other parameters. Check  [https://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux](https://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux)  for the detailed explanation and how to make the changes to the saa7134  module permanent.

To get the audio working:
sudo pactl load-module module-loopback
For more details check [http://linuxtv.org/wiki/index.php/Saa7134-alsa#Howto_use_Saa7134-alsa_with_Pulseaudio_based-system](http://linuxtv.org/wiki/index.php/Saa7134-alsa#Howto_use_Saa7134-alsa_with_Pulseaudio_based-system)

Cheers!

---

### Post by Bucky Ball on 2014-08-15
Excellent work! Please mark the thread 'solved' by following the second link in my signature to help others. Good luck. ;)

---

### Post by nargaroth_reg on 2014-08-15
It's done. Thanks for your concern regarding this issue.

---

