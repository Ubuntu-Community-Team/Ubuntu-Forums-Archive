---
title: "refuses to detect my i8x0-based sound chipset"
date: 2004-10-20
forum: Hardware &amp; Laptops
---

### Post by butters on 2004-10-20
I have a Centrino (i855GM) onboard sound chipset that it supported by the i810 alsa module.  The alsa init script is on the default runlevel.

GNOME says:
Sorry, no mixer elements and/or devices found

alsamixer says:
function snd_ctl_open failed for default: No such device

output of cat /proc/asound/oss/sndstat:
Sound Driver:3.8.1a-980706 (ALSA v1.0.4 emulation code)
Kernel: Linux profchaos.res.cmu.edu 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers: NOT ENABLED IN CONFIG


from lsmod:

snd_intel8x0m          18632  0
snd_intel8x0           33068  0
snd_ac97_codec         59268  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  3 snd_intel8x0m,snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  3 snd_intel8x0m,snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  10 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  1 snd

output of ls -l /dev/snd

total 0
crw-rw----    1 root     audio    116,   0 2004-10-18 14:05 controlC0
crw-rw----    1 root     audio    116,  33 2004-10-18 14:05 timer

there is no /dev/dsp

This laptop has working sound in every other distro I've tried.  What am I missing here?

---

### Post by triad169 on 2004-10-20
Sounds like similiar problem here:

[http://www.ubuntuforums.org/viewtopic.php?t=505](http://www.ubuntuforums.org/viewtopic.php?t=505)

---

### Post by cassidy on 2004-11-17
The link seems to be down  :cry:

---

### Post by mark_p on 2004-11-25
I have exactly the same problem. 
Its strange because sound WAS working. But now I show the same symptoms as reported here. 
I'm using a Dell Latitude D600 (Pentium M).

I'd really like to see a resolution to this.

---

### Post by fng on 2005-01-01
Same problem here with a SB live! 24bit card

---

### Post by clsdaniel on 2005-01-02
I got the same problem on my laptop, the problem is on he kernel, it sems ubuntu kernel maintainer compiled in an experimental driver, here is the trick:

1) Go to console (Gnome terminal for the matter)
2) Then execute the following command:

sudo rm /lib/modules/`uname -r`/kernel/sound/pci/snd-intel8x0m.ko

This should remove the file snd-intel8x0m.ko, which is the driver the stops your sound from working. Keep an eye on the comma, dont use this one ´, use the this `, or else it won't work.

Edit: Din't saw your kernel version, this one should work too:

sudo rm /lib/modules/2.6.8.1-3-386/kernel/sound/pci/snd-intel8x0m.ko

The problem is that ubuntu loads both, then normal driver snd-intel8x0 and the alternate experimental driver snd-intel8x0m, and both blocks each other, also the driver snd-intel8x0m.ko won't work.

Now reboot. Really! Reboot! :)

Good Luck

---

### Post by cassidy on 2005-01-04
The snd_intel8x0m module is not more loaded but alsa still say "alsactl: load_state:1134: No soundcards found..."   :cry:

---

### Post by Tiede on 2005-08-10
for the SoundBalster card, I might be able to help. Check out [ over here ](http://ubuntuforums.org/showthread.php?t=1805)
I will try to get more info for the other problems...

---

