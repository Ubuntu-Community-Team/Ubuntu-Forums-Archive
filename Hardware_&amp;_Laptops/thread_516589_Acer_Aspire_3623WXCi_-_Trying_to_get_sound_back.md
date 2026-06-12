---
title: "Acer Aspire 3623WXCi - Trying to get sound back"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by jis on 2007-08-03
Originally I began to play with drivers because microphone did not work. Now nothing sound related does work. Even alsamixer outputs only: "alsamixer: function snd_ctl_open failed for default: No such device"

According to Acer 3620 Series User's Guide, the laptop has Intel High-Definition audio support, so I followed instructions at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Added line "options snd-hda-intel model=acer" in /etc/modprobe.d/alsa-base, but I am not sure if it is the right model. 

lspci -v
```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Realtek ALC 655 codec (in Acer TravelMate 2410 serie laptop)
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at b0040800 (32-bit, non-prefetchable) [size=512]
        Memory at b0040400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```

I am using Xubuntu Feisty.

---

### Post by jis on 2007-08-05
I removed line "options snd-hda-intel model=acer" in /etc/modprobe.d/alsa-base.

Referring to [this AlsaWiki page]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-intel8x0"), I reinstalled the driver by running
```
./configure --with-cards=intel8x0 --with-sequencer=yes ; make ; make install
```
in the alsa driver directory. I also created ~/.asoundrc as suggested. I ran also these to insert the modules in kernel, but am not sure, if it is neccessary in ubuntu:
```
sudo modprobe snd-intel8x0 ; sudo modprobe snd-pcm-oss ; sudo modprobe snd-mixer-oss ; sudo modprobe snd-seq-oss
``` Rebooted.

Now playback works, but I still cannot record using microphone. I still wonder, why sound did not work at all, when using the driver as Intel High Definition audio.

---

### Post by jis on 2007-08-05
I want to add that I recall I could record my speech in Skype test call _some time_, before I installed non-default alsa in Feisty.

---

### Post by jis on 2007-08-06
I created audio group so that files in /dev/snd are accessible to wanted users.

```

$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```

$ cat /proc/asound/cards
 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with ALC655 at irq 17
```


I still can not record by audacity, for example:

Which device I should use for playback?
OSS: /dev/dsp
ALSA: Intel ICH6: Intel ICH6 (hw:0,0)
ALSA: Intel ICH6: Intel ICH6 - IEC958 (hw:0,4)
ALSA: front
ALSA: iec958
ALSA: spdif
ALSA: intel8x0

And which device I should use for recording?
OSS: /dev/dsp
ALSA: Intel ICH6: Intel ICH6 (hw:0,0)
ALSA: Intel ICH6: Intel ICH6 - MIC ADC (hw:0,1)
ALSA: Intel ICH6: Intel ICH6 - MIC2 ADC (hw:0,2)
ALSA: Intel ICH6: Intel ICH6 -  ADC2 (hw:0,3)
ALSA: front
ALSA: intel8x0

---

