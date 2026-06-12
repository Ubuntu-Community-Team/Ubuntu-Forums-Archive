---
title: "zoom g2.1 usb guitar multi effects pedal"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by jumbolkna on 2007-08-05
hey guys im fairly new to linux im running feisty i was just wondering how i could record via the pedal which on windows comes up as a usb audio device. i go to the hardware info page and i can see it come up as usb audio codec, usb alsa capture device. i was wonder how i could get it to record???? or even play music from it. i have an integrated ac97 with my mobo gigabyte k8nf9 nforce 4 mobo.. any help would be greatly appreciated

---

### Post by fredj on 2007-08-05
Open the alsa mixer (double click on the speaker icon) and go to the File->Change Device
menu.There you should be able to select your USB device as the default input and output.
Then any program you use which has been configured to work through Alsa will use this device.

---

### Post by jumbolkna on 2007-08-05
mm i just tried that however all i am getting is a playback tab with no recording option? perhaps it is not compatible with ubuntu? although when i go to system-> preferences-> sound i can choose to record with usb audio how ever when i try to it records blank????

---

### Post by fredj on 2007-08-05
What program are you recording with. Try Audacity and make sure before you start that it is also
looking at the right device.

---

### Post by jumbolkna on 2007-08-06
YES!! audacity worked a treat thank you soo much for all your help greatly appreciated! i was using the default recording software with ubuntu previously! but audacity is great thanks times a million

---

