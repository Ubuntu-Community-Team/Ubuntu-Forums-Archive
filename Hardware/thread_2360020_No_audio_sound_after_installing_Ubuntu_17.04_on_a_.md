---
title: "No audio sound after installing Ubuntu 17.04 on a new Dell XPS desktop"
date: 2017-05-01
forum: Hardware
---

### Post by marlonmin on 2017-05-01
Could somebody give me some clues how to debug this? The "Audio Volume" on the task bar looks normal. I can adjust the volume, but no sound. 

I bought a new Dell desktop computer. I really need to get the sound working. 

Thank you.

The command prints out:

[HTML]abigail@abilina:~/anaconda3$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC3861 Analog [ALC3861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[/HTML]

---

### Post by wildmanne39 on 2017-05-01
*Thread moved to **Hardware**.*

---

### Post by LastDino on 2017-05-01
One of my friends had old Dell lappy, where we could fix no audio issue with doing this>

Add this line to /etc/modprobe.d/alsa-base.conf

  ```
options snd-hda-intel model=dell-"your model Number"
```
  Then, restart alsa by entering the following in a terminal session

  ```
sudo alsa force-reload
```

You can then adjust volume output using "alsamixer" command in terminal as well.

There are different commands for adjusting output as well, but lets see if the thing works for you or not as you have newer version of Dell

---

### Post by marlonmin on 2017-05-01
Hi, LastDino,  some lines in the file look like:

[FONT=monospace][COLOR=#54FFFF]# Prevent abnormal drivers from grabbing index 0[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] bt87x index=-2[/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] cx88_alsa index=-2[/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] saa7134-alsa index=-2[/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-atiixp-modem index=-2[/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-intel8x0m index=-2[/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-via82xx-modem index=-2[/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-usb-audio index=-2[/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-usb-caiaq index=-2[/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-usb-ua101 index=-2[/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-usb-us122l index=-2[/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-usb-usx2y index=-2[/COLOR]
[COLOR=#54FFFF]# Ubuntu #62691, enable MPU for snd-cmipci[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-cmipci mpu_port=0x330 fm_port=0x388[/COLOR]
[COLOR=#54FFFF]# Keep snd-pcsp from being loaded as first soundcard[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-pcsp index=-2[/COLOR]
[COLOR=#54FFFF]# Keep snd-usb-audio from beeing loaded as first soundcard[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-usb-audio index=-2
[/COLOR]
I tried both:
[COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-hda-intel model=DELL-8910[/COLOR]

and 
[/FONT][COLOR=#FFFF54][FONT=monospace]options[/FONT][/COLOR][COLOR=#000000][FONT=monospace] snd-hda-intel model=DELL8910

And it didn't work. Should I also try the index=-2?[/FONT][/COLOR]

---

### Post by marlonmin on 2017-05-01
Also, how to use [FONT=monospace][COLOR=#000000]alsamixer to adjust volumes? I am attaching a screen shot for that.

My volume control on the taskbar seems normal. when I adjust it to the left or right, I can hear some sound, but I can't heard any sound when I watch a video on youtube.


[/COLOR]
[/FONT]

---

### Post by again? on 2017-05-01
When in alsamixer, press F1 for keyboard shortcut keys.

---

### Post by LastDino on 2017-05-01
Try this then

```

options snd-hda-intel model=basic
```

Instead of the line we tried previously.

Go to System>Preferences>Sound>Hardware. (should be under name system settings like windows)

On the Profile drop down menu, select "Analog Stereo Output".

Make sure the Output Volume is set to 100% and close.

Lets see if this works.

Although you already posted but just in case post output of
```
  cat /proc/asound/card0/codec#* | grep Codec 
```

and resolution of that image is quite low imo, I couldn't see anything with my sleepy tired eyes..

---

### Post by marlonmin on 2017-05-01
Fantastic, it woked!

What I did:
[FONT=monospace][COLOR=#FFFF54]options[/COLOR][COLOR=#000000] snd-hda-intel model=basic[/COLOR]
[/FONT]
Then, I right-click the "Audio Volume" control on the taskbar, then I change the HDMI audio port to built-in audio analog stereo.

Thank you.

---

### Post by LastDino on 2017-05-02
No worries mate, pleas mark the thread as "Solved" as suggested in link below my posts. It helps to keep solved threads clear from unsolved ones.

And welcome to Ubuntu forums, have a great journey.

---

