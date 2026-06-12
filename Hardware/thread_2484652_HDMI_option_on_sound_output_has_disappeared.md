---
title: "HDMI option on sound output has disappeared"
date: 2023-03-05
forum: Hardware
---

### Post by Olivares on 2023-03-05
I have 64-bit PC with both Ubuntu 22.04 and Windows 10. I use my Sony TV as a second monitor, connected by an HDMI cable. I normally leave the cable unplugged as otherwise the GRUB menu pops up on the TV, which is annoying. In the past 7 days the HDMI option has disappeared from the output options under 'sound' in Settings. On bootup I get the messages 'no AFG or WFG node found' and 'no codecs initialized.' How do I fix this?

---

### Post by professional-amateur on 2023-03-12
[B]THE CASE OF THE DISAPPEARING ALSAMIXER HDMI AUDIO

[/B]Having same problem on a 64 bitt Ubuntu 22.04.1. It all started -meme here- I think when I connected my 2nd hdmi monitor a few days ago. I use 1 hdmi full time for TV monitor and sound and a second hdmi port for projector. After enjoying a movie on the projector my option to output sound back to my hdmi monitor disappeared from the list of selectable devices. Now only the headphone built in audio is available. Also alsamixer disappeared as well. When typing alsamixer in terminal the result does not pull up the mixer like it always has. Now it reads back: 
ALSA lib confmisc.c:855:(parse_card) cannot find card '0'
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_card_inum returned error: No such file or directory
ALSA lib confmisc.c:422:(snd_func_concat) error evaluating strings
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1334:(snd_func_refer) error evaluating name
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:5701:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib control.c:1528:(snd_ctl_open_noupdate) Invalid CTL default
cannot open mixer: No such file or directory


I also got the "no AFG or MFG" message when booting.
When typing aplay -l into terminal i get:
**** List of PLAYBACK Hardware Devices ****
card 1: Generic [HD-Audio Generic], device 0: ALC221 Analog [ALC221 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

All trouble shooting - rebooting, disconnecting hdmi, rebooting, reconnecting hdmi, rebooting, connecting to different port, rebooting - no results.
Yes, alsamixer is in computer/usr/bin/alsamixer.
Yes sudo ubuntu-drivers autoinstall command results in: All the available drivers are already installed.

Somehow connecting the 2nd hdmi causes all hdmi (spdf) to get "*blocked*?" Reinstalling fresh Ubuntu worked in bringing hdmi audio output back but then I plugged by 2nd hdmi back in to watch a movie again today. **POOF!** Alsamixer cannot find card 0. Hdmi sound output option disappeared.

Any help here would be hot.

---

