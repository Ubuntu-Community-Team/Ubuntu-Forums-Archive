---
title: "Bad Sound with HP Pavilion DM3-1130us Laptop"
date: 2010-12-09
forum: Hardware
---

### Post by tyr14 on 2010-12-09
At first, thank you for reading and try to help me to solve this problem...

Im using Ubuntu 10.10...

Microphone isn't working

Speaker isn't working fine... It is just working with volume at 50%...
If I want to get louder, the music or video start to blink(skip) the sound... I mean is not working how should it be.
[U]-IN FACT, WITH WINBUGS 7 IS WORKING TERRIFIC-
THE PROBLEM IS WITH UBUNTU[/U]...:( 
(I'm sorry because English isn't good)

I've heard about this:
$sudo nano /etc/modprobe.d/alsa-base.conf
and add at the end
options snd-hda-intel model=MODEL (I've tried hp-dv5, hp-dm3, dell-s14, the last works with a lot of people)

griffin@Griffin-Notebook ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

griffin@Griffin-Notebook ~ $ head -1 /proc/asound/card0/codec*
Codec: ***_IDT 92HD81B1C5_***

I think the problem is with this IDT codec, I was looking for this
but i don't found the solution... A lot of people had the respective solution with their laptops, but I don't...

Thank you for your help...

---

### Post by tyr14 on 2010-12-12
Well, if someone was looking for help me... Thank you...

The solution with the sound HP DM3 1130US was:

1 - I had to format my Laptop and I've Installed Windo$s 7...
(I've just did this because I can't run my Starcraft 2 as well with ubuntu)

2 - With Window$, I've installed the bios upgrade from HP
2010-05-21 , Version:F28 A, 2.2M - This fixes some audio issues too...
(I did a test without the IDT Driver Codec in Win... And Sound it's bad too)
When we install the IDT Driver from HP, the sound is out of the box :D

3 - I downloaded the Ubuntu Iso 10.10 again, and install again from 0.
And with the latest ALSA Drivers sounds fine...

And modify the alsa-base.conf file with this lines:
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=dell-s14

Then, System/Preferences/Sound/Hardware
"Analog Surround 4.0 Output + Analog Stereo Output"

And the sound is very loud, I think better than Windows...

P.S. With Win7 the sound has no problem, BIOS no matter, but with linux, sound sucks... then, if somebody has the same problem... Check HP Bios Utility... DON'T RUN WITH WINE...

---

