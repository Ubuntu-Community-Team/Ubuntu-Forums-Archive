---
title: "Asus Xonar U5 SPDIF out as default"
date: 2018-01-17
forum: Hardware
---

### Post by alex346 on 2018-01-17
Hello,
As I have tried lot of manuals from the internet and lot of forum advices now, I am not sure where I am.

What I would like to obtain:
best > possibility to choose between the default audio device from GUI - 2ch HDMI in the Asus chipset (motherboard), or 5.1 SPDIF out in the Asus XONAR U5 (USB).
good> 5.1 channel SPDIF out via the Asus Xonar U5 USB

I need only outputs, don't want to use any inputs.

I have to done somethng what disabled me GUI controls in Gnome, but alsamixer works ok. I don't know what I have done.

As a root, I can choose specific out in the smplayer prerferences and send there 2ch audio - then the audio coming from my 5.1 system(but only stereo).

When I am editing /etc/asound.conf I am putting:
```
pcm.!default {


 type hw
 card 1
 device 1
}


ctl.!default {
 type hw
 card 1
# device 1
}
```

As the aplay -l gives me ```
root@ubu-4690:~# aplay -l | grep U5  
card 1: U5 [ASUS XONAR U5], device 0: USB Audio [USB Audio]
card 1: U5 [ASUS XONAR U5], device 1: USB Audio [USB Audio #1]
card 1: U5 [ASUS XONAR U5], device 2: USB Audio [USB Audio #2]

```

And at the nearest restart number of this card is swapped with the other card, and U5 comes as:
[alsamixer in that state needs to choose the Xonar card, as the fisrt one is another one]
```
root@ubu-4690:~# aplay -l | grep U5  
card 3: U5 [ASUS XONAR U5], device 0: USB Audio [USB Audio]
card 3: U5 [ASUS XONAR U5], device 1: USB Audio [USB Audio #1]
card 3: U5 [ASUS XONAR U5], device 2: USB Audio [USB Audio #2]
```

That is the full output of the aplay -l```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI_1 [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI_1 [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI_1 [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: U5 [ASUS XONAR U5], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: U5 [ASUS XONAR U5], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: U5 [ASUS XONAR U5], device 2: USB Audio [USB Audio #2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Is there something what I can do now?
Where should I start to troubleshoot?

regards

---

### Post by dark-helmet-chris on 2018-01-28
I know this is sort of a silly response, but... here's how I typically solve this when I break something. I have done all sorts of X server edits, audio system edits, mdm and lightdm edits, etc. Once in a while I break something and I can't figure out how to get back to where I was originally. Of course, one never makes little backups before trying these things because "I'm sure I won't break it." hehe. I think we've all been there. So, what to do? Well...

When I break something:
- shut down and remove the connection to the hard disk
- install some temporary hard disk - doesn't matter what size or speed
- do a fresh install - the installer makes all the default configs for me :)
- copy all the default configs to some removable media / network location / whatever you like.
- shut down and reconnect your real hard disk
- review your config files and compare to the "new originals" you now have.

Usually, this gets me back to operational. It's a sort of "run around the border" to get there, but it's better than wasting 3 days until I realize my mistake that's probably staring me in the face.

---

### Post by User-007 on 2018-01-31
I have a setup that you’d like to achieve as the best result.

BTW, noticed that sound system is very easy to break. So I suggest to restore asound.conf file into its original state before proceeding.

And you did not mention which version of Ubuntu you have, but I think you have a Gnome edition.

So, take a look here: [https://ubuntuforums.org/showthread.php?t=2381055](https://ubuntuforums.org/showthread.php?t=2381055)

And install this: [https://extensions.gnome.org/extension/906/sound-output-device-chooser/](https://extensions.gnome.org/extension/906/sound-output-device-chooser/)

Fixed now?

User JB

---

