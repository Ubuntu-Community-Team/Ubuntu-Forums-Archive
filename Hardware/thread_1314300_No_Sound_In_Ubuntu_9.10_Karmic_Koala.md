---
title: "No Sound In Ubuntu 9.10 Karmic Koala"
date: 2009-11-04
forum: Hardware
---

### Post by Danjay5291 on 2009-11-04
Hi all.

I just removed from Windows Vista to Ubuntu 9.10 today.   I have had Ubuntu before but not since 7.10 and not on this laptop.   My current laptop is a Asus F5R.   Everything seems to be working fine except the sound.  My sound card is a built in Realtek ALC 660D.

The first thing i did was head to the Realtek website and download their linux drivers.  I tried both the automatic and manual way of installing the drivers but both times got the error "./install: 102: alsaconf: not found".   After some searching I discovered that alsaconf is no longer included in Ubuntu so my question is this:

How do I get the sound working?


Thank you all very much in advance :)

---

### Post by Intel91 on 2009-11-04
To avoid making another post I would like to say that my sound doesn't work either. However, when I first loaded up Ubuntu 9.10 everything worked, then I updated and installed my ATI HD2600 and network drivers. Restarted, sound stopped working. I checked my sound settings and it recognizes zero hardware devices, and is outputting to "dummy output." I used to use Ubuntu exclusively, but it has been a long time now and I forget how to do many things, so I can't confirm my sound card except to say I have an Asus F8SA laptop and have a realtek sound card. If someone can remind me how to check the hardware and confirm my sound card that would be appreciated. Restarting doesn't fix the problem, killing pulse and looking for hardware doesn't either. It worked, now its not. 

Thanks.

---

### Post by Celestika6 on 2009-11-04
Same issue here. No sound on startup, no sound for my games and no sound for my media players or alerts. :s

---

### Post by Intel91 on 2009-11-04
I troubleshot my personal problem down to one of my hardware drivers, after toggling and restarting one at a time I will post back with which one(s) are causing my problem. I have a feeling it is my software modem driver.

---

### Post by Intel91 on 2009-11-04
Solved for me. My problem was the software modem driver, if it is installed under hardware drivers my sound won't work. I guess it is worth a try for you guys to go under System>Administration>Hardware Drivers to see if you have "software modem" driver installed, and if so disable it.

---

### Post by Esk1m0 on 2009-11-04
Disabling the hardware driver worked for me as well... :)

---

### Post by gnomicon on 2009-11-18
i've got an asus f8sa too, hopefully sound is working now after disabling the software modem, thanks (i was about to become angry against ubuntu)

still have problems with wlan led always lit though... :/ 
hope the transmitter is switched off anyway..

---

