---
title: "sound disppeared"
date: 2010-03-24
forum: Hardware
---

### Post by mongoose_za on 2010-03-24
Hi,

I have a laptop with onboard speakers and a headphone jack.
If you use the headphone jack the onboard speakers stop.

This is good because my onboard speakers are broken so i plug my headphones into the headphone jack and i still have sound :D 

The problem is. During the process of trying to get my webcam to work I installed ekiga. After this my sound disppeared. I've gone to the sound preferences in ekiga and tried all the different output options but still i have no sound. 

How to get my sound back and how can I reinstall my network drivers?

Any suggestions would be greatly appreciated.

---

### Post by optimusmedia on 2010-03-24
This may not help, but in trying to troubleshoot an issue with speakers and headphones both playing at the same time, 9.10 replaced my sound card as "dummy output" and I got nuthin'  Anyway, after days of research, i reinstalled the latest linux-image from Synaptic. One reboot later and I'm back with sound. 

Hope that helps.. I'm still trying to shut off the laptop speakers when headphones are in..

---

### Post by mongoose_za on 2010-03-25
thanks optimusmedia for your reply. I figured I might have to reinstall because originally I did have the sound working. Bothers me though that every time I run into some kind of issue I need to reinstall -_-

As for shutting off your  laptop speakers, just poor tea over them :D

---

### Post by mongoose_za on 2010-03-26
Heya

Hope this helps someone.
I fixed my issue by going to
Administration -> Hardware Drivers -> And here I disabled some proprietary drivers that my internal modem was using.
I fixed the network card by restoring disabling my lan card in my bios rebooting. Then enabling it and rebooing again.

---

