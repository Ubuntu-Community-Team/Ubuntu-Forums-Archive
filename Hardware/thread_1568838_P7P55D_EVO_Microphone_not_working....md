---
title: "P7P55D EVO Microphone not working..."
date: 2010-09-05
forum: Hardware
---

### Post by dankdank on 2010-09-05
Hi there community, i'm having an issue with my 10.04 ubuntu install. The microphone is not functioning i made sure the mic was not muted in sound preferences, alsamixer, and pulse audio.

I have been searching around for the past 4-5 hours trying to find a fix but to no avail.

when I run alsamixer in terminal it says my chip is: VIA VT1828S and my card is: HDA Intel

I also tried to apply this line to my 
/etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel position_fix=1
```

If anyone can please help me with this issue i would appreciate it!

---

### Post by dankdank on 2010-09-06
Adding this just in case its of importance. ;)

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1828S Analog [VT1828S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1828S Digital [VT1828S Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic_1 [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by dankdank on 2010-09-06
I SOLVED IT!!!

Here is what I did if anyone else was having this issue!
(i'm not sure which one fixed it but i ran both of these fixes to be sure)

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
sudo apt-get install linux-sound-base alsa-base alsa-utils 
sudo apt-get install gdm ubuntu-desktop
```

```
apt-get install linux-backports-modules-alsa-lucid-generic
```

---

