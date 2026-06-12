---
title: "Does not work with webcam microphone"
date: 2009-07-14
forum: Hardware
---

### Post by harry71194 on 2009-07-14
Hi, I have used Ubuntu for a bit now, and there is just one thing that annoys me: I can not get my webcam's microphone working.

I have a Microsoft Lifechat 3000 headset for listening to everything on the PC, etc etc, and it works fine after I followed [these steps]("http://ubuntuforums.org/showthread.php?t=402293").
But, on the headset, the microphone is broken, so I plugged a Microsoft Lifecam 6000 in, to use it as a microphone. But, it does not want to be used I guess. It does not use it.
When I
`less /proc/asound/modules, I get:

0 snd_usb_audio
1 snd_usb_audio

That is bad. I commented out the second usb_audio, and that fixed my hearing, but then obviously disabled my microphone. If I go to enable the other device to load [both usb_audios], then NOTHING works. ;_;

So help me to be able to run 2 USB audio devices, one a microphone, and one a headset, with a broken microphone, please.

---

### Post by ozanamn on 2009-07-14
Hey,

Maybe you could try Pulseaudip Device Chooser.

Here
[http://0pointer.de/lennart/projects/padevchooser/](http://0pointer.de/lennart/projects/padevchooser/)

Let me know if this works out for you 

Oz

---

### Post by harry71194 on 2009-07-14
> **ozanamn said:**
> Hey,

Maybe you could try Pulseaudip Device Chooser.

Here
[http://0pointer.de/lennart/projects/padevchooser/](http://0pointer.de/lennart/projects/padevchooser/)

Let me know if this works out for you 

Oz
Oh nice, it detects it and lets me set it as default, etc. Is there a way I can disable Alsa? Like totally, and only use the Pulseaudio? Some programs don't like to listen to Pulseaudio. :3
ie, I have the USBWebcam selected as default and checkmarked as such, yet it still tries to use my headset's mic.

---

### Post by ozanamn on 2009-07-16
Bump

---

### Post by harry71194 on 2009-07-17
Okay, for some reason, my headset isn't working now, and often the pulseaudio process will spike to 100% cpu.

---

### Post by harry71194 on 2009-10-29
Well, I killed pulse and am using alsa now. The webcam still doesn't work, and I think it's because it's a Micros*** webcam =P

Got a new open-source one. Working now!

---

