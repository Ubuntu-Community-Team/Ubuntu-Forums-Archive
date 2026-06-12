---
title: "Sound is not working, What do I do ?"
date: 2011-04-19
forum: Hardware
---

### Post by Nikolai508 on 2011-04-19
I recently installed Ubuntu on my ASUS N53J G and I tried out some music and videos on youtube and there is absolutely no sound.

I had a look at the troubleshoot pages on the ubuntu help site and I did not understand most of it but I tried some of the tests that it said and it seems that the hardware is recognised as it says that their is a intel HDA showing up in the terminal when i type in:

lspci -v | less

I have no idea on how to fix this problem, can someone give me something to do thats a little more understandable for me please. I am new to ubuntu (and linux) you see.

this is the help site I was using : [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I am using Ubuntu 10.10 64 bit

I am not so sure about the exact hardware I am using, but all I can see on my laptop is that it says "Sonic Master - Audio by bang & Olufsen"

---

### Post by Paul41 on 2011-04-19
See if installing the restricted extras fixes it.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Nikolai508 on 2011-04-19
Nope it still doesn't work, thanks for reply though :D

---

### Post by Paul41 on 2011-04-19
Do you have any sound at all?  For example do you hear the systems sounds (like when you log in) or is the sound problem only with music and youtube?

I was having a problem with no sound at all on one of my computers.  I tried all kinds of things to fix it.  I eventually gave up and installed Debian.

---

### Post by Jose Catre-Vandis on 2011-04-19
Report back on the output of
```
aplay -l and aplay -L
```in a terminal

---

### Post by Nikolai508 on 2011-04-19
aplay -L gave me this;

```
default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC259 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC259 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC259 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC259 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC259 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC259 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC259 Analog
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC259 Analog
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC259 Analog
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC259 Analog
    Hardware device with all software conversions

```


aplay -l gave me this 

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also to the other guy I get no sound at all, from anything.

---

### Post by Yellow Pasque on 2011-04-19
Try this: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)
If it doesn't work, post your alsa-info using the script provided in that thread.

---

### Post by Nikolai508 on 2011-04-20
My sound is still not working after running the scripts from that link.

This is my Alsa info;
```
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Apr 20 2011 for kernel 2.6.35-28-generic (SMP).

```

This is aplay -l ;

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

The sound tests that they said to perform ran, but they did not emit any sound whatsoever, and I made sure that the volume was full and not muted. I have no idea what to do now.

Is there anything else I can show that might help you help me :)

---

### Post by Toz on 2011-04-20
How about this?
[http://blog.tersmitten.nl/archives/1082](http://blog.tersmitten.nl/archives/1082)

---

### Post by Paul41 on 2011-04-20
I filed a bug about this a long time ago. After answering some initial questions I never heard anything else on the bug. There was never a fix and the bug now seems to be deleted. This is why I gave up and installed Debian on the computer I was having a problem.

---

### Post by lidex on 2011-04-21
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Jose Catre-Vandis on 2011-04-21
Can you run (in a terminal again):
```
alsamixer
```
if not try
```
sudo alsamixer
```

Are sound levels set correctly?

If it only works with sudo, you may need to add yourself to the audio group

---

### Post by Nikolai508 on 2011-04-21
I will these things out, thanks for replying. 

I can't try it immediately I am on Windows at the moment :D

I am not so confident in this working to be honest, but I am willing to try to get it working though. Thanks for your input and suggestions everyone :D

---

### Post by Nikolai508 on 2011-04-22
[http://www.alsa-project.org/db/?f=49091e8b7eb99f2be868497306aafa21723b6912](http://www.alsa-project.org/db/?f=49091e8b7eb99f2be868497306aafa21723b6912)

There is the link to my computer information,

The sound actually started working for like 5 minutes as it made a noise when I logged in and then I played a video on youtube to test it their to.

Then suddenly the sound stopped working again, Ubuntu sure is being an awkward boob :D

---

