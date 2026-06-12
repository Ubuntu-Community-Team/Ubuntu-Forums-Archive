---
title: "headphones not detected in Ubuntu 16.04"
date: 2018-06-22
forum: Hardware
---

### Post by gleedadswell on 2018-06-22
Audio was working just fine until a couple of days ago.  Then my audio completely failed (no sound at all through any device, sound settings just showed "Dummy output" as the only option for "play sound through").  Following some advice on the forums, I updated the BIOS.  That has restored my sound except that headphones or speakers plugged into the jack are not detected.  On sound settings they don't show up as one of the entries in "play sound through".  Normally, before when I plugged in headphones a dialogue box would automatically pop up asking whether I had plugged in headphones, a microphone or a headset.  That dialogue isn't popping up any more when I plug something into the jack and I still get sound from the speakers (and not from the headphones) when I plug in headphones.  The headphones also don't show up in pavucontrol.  Clicking on "port" the only item in the dropdown list is Speakers.

I have already looked at and followed advice from a number of other posts, including:

[https://askubuntu.com/questions/920709/ubuntu-16-04-doesnt-recognize-the-headphone-anymore-no-guide-seems-to-work](https://askubuntu.com/questions/920709/ubuntu-16-04-doesnt-recognize-the-headphone-anymore-no-guide-seems-to-work)
[https://askubuntu.com/questions/132440/headphone-jack-not-working](https://askubuntu.com/questions/132440/headphone-jack-not-working)
[https://ubuntuforums.org/showthread.php?t=2384222&highlight=headphones](https://ubuntuforums.org/showthread.php?t=2384222&highlight=headphones)


In particular, I've already tried killing and restarting pulseaudio, editing [COLOR=#111111][FONT=Consolas]/usr/share/pulseaudio/alsa-mixer/paths/[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]analog-output-headphones.conf, [/FONT][/COLOR]issuing alsactl restore, etc.  I've also tried reinstalling pulseaudio.

Here are some system details:

```

geoff@kubo-mobile:~$ uname -a
Linux kubo-mobile 4.4.0-128-generic #154-Ubuntu SMP Fri May 25 14:15:18 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

My hardware is reported by System Details as:

Processor:  Intel® Core&#8482; i5-7300HQ CPU @ 2.50GHz × 4 
Graphics: GeForce GTX 1050/PCIe/SSE2

I'm now going to post some of the info recommended by the sound troubleshooting guide at [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure).  The output from alsa_info.sh was posted here:

[http://www.alsa-project.org/db/?f=0d66122bdffa30bea69da1109c97654481658470](http://www.alsa-project.org/db/?f=0d66122bdffa30bea69da1109c97654481658470)

Anything else I can post to help diagnose this?  Thanks!

---

### Post by Yellow Pasque on 2018-06-23
If possible, can you remove this line, reboot, and run the alsa-info script again?
```
snd_hda_intel: patch=hda-jack-retask.fw,hda-jack-retask.fw,hda-jack-retask.fw,hda-jack-retask.fw
```

I think you want to see a headphone out here:
```
[   20.812120] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC3246: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   20.812122] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   20.812124] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   20.812125] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
```

You could also try updating your sound modules/driver:
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
Or perhaps try a LiveUSB of Ubuntu 18.04 if you want to try a more recent kernel without modifying your current install.

---

