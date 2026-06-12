---
title: "Rocketfish USB Gaming Headset"
date: 2008-11-26
forum: Hardware
---

### Post by supersteviobros on 2008-11-26
I have a Rocketfish USB Gaming Headset - it has earphones and a microphone.
I'm trying to get this to work in Ubuntu. It seems to recognize that a USB audio device is connected, because when I connect it and go to the volume control, there is an option for selecting "USB Device 0xd8c:0x0c (Alsa mixer)" and there are volume controls for audio and mic

The only part that works is the mic feed, i.e. I can turn on the mic and hear my voice through the headset, but when I try to listen to something like a Youtube video, there is no sound in the headset, but it plays through the speakers

I've tried connecting it while the OS is running, and before I turn on the computer, with the same results.

---

### Post by starcannon on 2008-11-26
I use a logitech USB headset, and find that I have to fiddle about with the sound settings:
System>Preferences>Sound
I usually set it to my USB sound device in each of the drop downs, set it to the default mixer device, and get success that way. A little trial and error with this will likely get you rolling.

GL

---

### Post by markbuntu on 2008-11-26
I use the pulseaudio volume control (pavucontrol) for my usb headset, my usb webcam, and my two sound cards. It makes life very easy.  More on that here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

