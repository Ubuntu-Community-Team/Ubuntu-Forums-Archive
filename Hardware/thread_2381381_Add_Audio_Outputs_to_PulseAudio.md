---
title: "Add Audio Outputs to PulseAudio"
date: 2017-12-30
forum: Hardware
---

### Post by Owen_Murphy on 2017-12-30
I recently installed Lubuntu on a Zotac Zbox CI325-Nano machine, and I have been unable to use most of the audio outputs with PulseAudio.  The 1/8" line out jack works fine, but none of the other outputs work with pulseaudio (HDMI, optical). 

I was able to find the HDMI hardware and play audio through it using the aplay command, so I know that the hardware works:
```
aplay -D plughw:0,8 /usr/share/sounds/alsa/Front_Right.wav
```
 
However when I manually added the hardware to the /etc/pulse/default.pa file, I could not get it output audio from the HDMI port.  I restart pulseaudio several times and rebooted the computer several time with no luck.  In fact, after I added the HMDI port to default.pa, there was a faint high-pitched hum coming from the HDMI.

This is the line I added to /etc/pulse/default.pa:
```
load-module module-alsa-sink device=hw:0,8
```

So my question is: how do I add additional audio hardware to pulseaudio so that I can use it as an audio output?

Thank you.

---

### Post by heysoundude on 2018-01-10
I think we need a little bit more info about what you're trying to accomplish, other than sending audio out via HDMI.  (I have lubuntu on a zbox as well; it's what I'm typing this on, actually)
I suspect the device you're sending the audio to may be older and might have an HDMI interface that is video only.  The "old" 720p LCD TV repurposed as a monitor I'm looking at right now is like that; I prefer to use headphones, so it's not a major imposition or issue.

---

