---
title: "No sound - Asus X59SL  HDA SIS 966 - Chip: Realteak ALC660-VD."
date: 2009-03-03
forum: Hardware
---

### Post by iBurger on 2009-03-03
I hope somebody can help me. 
- Ubuntu Hardy, 8.04.

About the Asus X59SL Laptop (also branded as F5SL)
- Integrated audio: HDA SIS 966 - Chip: Realteak ALC660-VD.

Things I have done;*
- checking/un checking "Headphone" switch in the Gnome volume control.
- installed alsamixer, made sure everything is maxed out.

- ran the following code based on this [thread]("http://ubuntuforums.org/showthread.php?t=667586"): 

```
sudo update-pciids
sudo lspci | grep Audio
```

- result was:
```
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
```

- changed the **/etc/modprobe.d/alsa-base** but no success so far.
added the line "options snd-hda-intel model=laptop".

- followed the tips on [Soundtroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") page. Device is recognized.

**aplay -l **

```

**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


[B]lspci -v | less
[/B]

Screenshots:
[http://i42.tinypic.com/2ykkxtf.png](http://i42.tinypic.com/2ykkxtf.png)
[http://i44.tinypic.com/f50qx2.png](http://i44.tinypic.com/f50qx2.png)
[http://i43.tinypic.com/2vvlw9c.png](http://i43.tinypic.com/2vvlw9c.png)

---

### Post by hotweiss on 2009-03-03
Add this line to /etc/modprobe.d/alsa-base:

> options snd-hda-intel position_fix=1 model=lenovo

and delete the other line you added. Finally restart your computer.

---

### Post by iBurger on 2009-03-03
[SIZE="7"]:)[/SIZE]

Thank you! Works great!

---

### Post by zimbardo on 2009-10-09
Hi, 

I have the same problem with ASUS F5SL under Mandriva Linux 2009 Spring. I did all mentioned steps but it didn't help. 

In my case the lack of sound is not permament. Sometimes when I use Linux I do have sound, sometimes I do not. It seems to happen quite at random. I noticed that when the sound works Sound Mixer under KDE shows HDA SIS 966 as a sound device, and when it doesn't work i shows Realteak ALC660-VD.

Another clue may be that under GNOME when there is no sound when I choose "Sound Preferences" and then "Output" the only option for a sound device for sound output I have ist "Null output"

Any ideas?

Greetings

---

### Post by XavierSythe on 2009-11-28
I have the exact same system specs and issues!!
Someone solve this ASAP!!!

---

### Post by blikkies on 2009-12-12
This worked for me - from [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/472235](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/472235)
 

 Please check that the devices in your mixer are un-muted. According to your settings, although they are set to full volume, they are still muted.
 Go to SYSTEM, Preferences, Sound
 

 Thanks for the help.:D

---

