---
title: "Unable To Get Sound Working to External Speaker on HP TouchSmart 320 on Ubuntu 11.04"
date: 2011-11-09
forum: Hardware
---

### Post by johnmarkschofield on 2011-11-09
This is an HP TouchSmart 320, model number 320-1200m. I'm using Ubuntu 11.04, fully-updated.

Hardware information:

[INDENT]root@hp320:/home/mpower# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

root@hp320:~$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: IDT 92HD91BXX[/INDENT]

Sound to headphone jack works properly, but sound to built-in speakers does not work. I have installed Windows, and with Windows 7 installed, all audio hardware works properly, so this isn't a hardware fault.

I've looked at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and have been unable to find my card in [http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt) .

I have tried adding almost every conceivable model in the line "options snd-hda-intel model=MODEL" line I added to /etc/modprobe.d/alsa-base.conf.

Update 2011-11-09 2:31 PM PST: I've gone to Control Center -> Sound Preferences to attempt settings that make sound work. The "Hardware" tab shows one device: "Internal Audio 1 Output / 1 Input Analog Stereo Duplex." There are two output profiles listed in the selection box at the bottom of the tag: Analog Stereo Duplex and Analog Stereo Output. Neither cause sound to emit from the speakers.

I've also run alsamixer on the command-line and ensured that everything is set to maximum and nothing is muted.

Update 2011-11-09 5:15 PM PST: I've replicated the exact same symptoms in 11.10.

---

