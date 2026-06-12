---
title: "USB M-Audio Fast Track as USB Headphones?"
date: 2016-07-07
forum: Hardware
---

### Post by dante3 on 2016-07-07
I own a Dell Vostro 1700, vintage 2008. I recently installed Lubuntu 15.10, to help the old girl cope with the reality of age. However, to my chagrin, I can no longer use my M-Audio Fast Track recording interface as a USB headphone jack, as I used to on Windows (my standard headphone jack fried itself around 4 years ago, and replacing the part did nothing to fix it). Any insight on how I can easily configure Lubuntu to route my system audio through the USB device?

Any help would be greatly appreciated. :D

---

### Post by QDR06VV9 on 2016-07-07
Hi dante3....without knowing what you have done yet?
Try installing pulseaudio volume control
```
sudo apt-get install pavucontrol
```
And try to find the device in the Configuration Tab
If that is useless..give us the output from this in the terminal
```
aplay -l
```
And
```
lsusb
```
As we try to figure this out.

---

### Post by dante3 on 2016-07-07
Runrickus, thanks for the quick reply.

In the Config tab of PulseAudio, both Built-In and M-Audio Fast Track are displayed. Both are set to Analog Stereo Duplex. I've turned Built-In to "Off;" which setting should I use for the USB? The options are various combinations of Digital Stereo (IEC958) input, Analog Stereo Input, Digital Stereo (IEC958) Output, Analog Stereo Output, Analog Stereo Duplex and Digital Stereo (IEC958) Duplex.

EDIT: Digital Stereo Output seems to have worked. Thank you for your help.

---

### Post by QDR06VV9 on 2016-07-07
Nice! Glad it worked out. We always like it when it is easy.:D
Kind Regards

---

### Post by ajgreeny on 2016-07-07
Great! Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

