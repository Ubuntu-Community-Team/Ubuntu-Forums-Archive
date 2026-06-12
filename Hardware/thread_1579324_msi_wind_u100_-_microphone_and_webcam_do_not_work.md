---
title: "msi wind u100 - microphone and webcam do not work"
date: 2010-09-21
forum: Hardware
---

### Post by Aahz on 2010-09-21
Hi guys and gals,

I have installed ubuntu remix on my msi wind u100. It is great, aside from one  thing, the microphone is not working. I have 10.04 lucid lynx edition. Fortunately, no flickering screens or other big problems.

But I desperately need the microphone to work, I must use it on skype. I tried installing a "backport" package, which did nothing. I also installed the gnome alsa mixer. In there I can see the two microphone ports, but unmuting or moving the sliders does absolutely nothing for me. My skype only shows me the pulseaudio server - nothing else. the main sound program (on the taskbar) does not recognize any microphones. Even though it should find two - the built in one and the external one.

Any ideas on where to begin fixing it?

---

### Post by Aahz on 2010-09-22
Bump, if I may.

---

### Post by pcolamar on 2010-09-22
+1

I have just the same problem and I cannot use Skype
I do not know if this has something to do with the fact Lucid uses Pulseaudio instead of Alsa.

---

### Post by Aahz on 2010-09-22
Well, I cannot even use the sound recording program, for that matter. 

I do think the problem is indeed in the Pulseaudio vs. Alsa usage, though. I remember that the microphone worked just perfectly on an older version of Ubuntu I used a while ago (probably it was 9.xx). 

Confirming that is also the fact that the ALSA mixer sees two microphone ports, which is correct, as the netbook has one internal microphe and a jack for an external one. However, fiddling around with the switches does absolutely nothing for me. Not in the sound recorder and not in skype either. Hell, even in the pulseaudio tab that is on the taskbar there NO microphone detected, at all.

Any ideas? We are now two and I am sure there are more, as there must be lots of people who use MSI wind with the UNR and I bet someone has found/done a workaround.

HALP!

---

### Post by pcolamar on 2010-09-22
Aahz,
 what's your problem with webcam ?

---

### Post by Aahz on 2010-09-23
> **pcolamar said:**
> Aahz,
 what's your problem with webcam ?

It just will not detect. The Fn keys for turning it on and off do absolutely nothing. The photobooth also reports no devices. However, the webcam issue is secondary to the microphone one.

---

### Post by Aahz on 2010-09-23
OK, I just solved it! Halfway. 

Go to Sound Preferences. Go to Hardware. Change Profile from analog stereo output to analog stereo duplex. This enables the microphone jack for usage. I have no idea why the default setting would leave it at only output and not full duplex mode. 

Anyhow,this still leaves the internal microphone and the webcam inoperable. I assume that the webcam is more of a driver problem? I could care less about the internal microphone, because its recording quality is pretty bad.

---

### Post by pcolamar on 2010-09-24
This problem for me was just the fact that the Fn+F6 had to be kept pushed for 2 seconds to work.
I guess you have checked with lsusb to see  if the camera is on or not.
(my lsusb below):
Bus 005 Device 002: ID 0db0:a97a Micro Star International Bluetooth EDR Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 004 Device 047: ID 5986:0203 Acer, Inc** *this is the camera*
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by pcolamar on 2010-09-24
> **Aahz said:**
> OK, I just solved it! Halfway. 

Go to Sound Preferences. Go to Hardware. Change Profile from analog stereo output to analog stereo duplex. This enables the microphone jack for usage. I have no idea why the default setting would leave it at only output and not full duplex mode. 

Anyhow,this still leaves the internal microphone and the webcam inoperable. I assume that the webcam is more of a driver problem? I could care less about the internal microphone, because its recording quality is pretty bad.


Well, for the micro, I have solved like you and I am using an external microphone due to the bad quality of the internal one.
For the Webcam, I answered before.
Mine is working in skype and Cheese although is stops working randomically, in this case I need to turn it off and back on (2 times Fn+F6 ) to get it work .

Cheers

Palmer

---

### Post by Aahz on 2010-09-24
woo, thanks for that! The buttons do work and activate the cam, just the yellow light does not turn on like it would in windows. But by watching lsusb, I managed to get it to work. Mine is actually a Microdia(and especially crappy version, it seems, superior only to the bison one which messes up USB). Photobooth recognized it just fine after I turned it on by watching lsusb.

I guess this thread can have the [solved] tag:)

---

### Post by pcolamar on 2010-09-24
Yep, Aahz.
Tag it has [Solved]

Till next time ....
Palmer

---

