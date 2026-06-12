---
title: "Very low sound in Ubuntu 13.04 (ALC275)"
date: 2013-07-05
forum: Hardware
---

### Post by bug80 on 2013-07-05
The sound in Ubuntu 13.04 is *very* low on my machine, and even inaudable when using speakers. My laptop is a Sony VAIO SVS1513M1EW.

Output of 'aplay -l':

```
*** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: PCH [HDA Intel PCH], apparaat 0: ALC275 Analog [ALC275 Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: PCH [HDA Intel PCH], apparaat 3: HDMI 0 [HDMI 0]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: PCH [HDA Intel PCH], apparaat 7: HDMI 1 [HDMI 1]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0

```

Outout of ' lspci -v | grep hda'

```

Kernel driver in use: snd_hda_intel

```

What I've tried so far:

[LIST]
[*]Playing with the levels in pulseaudio
[*]Turning up all the channels in alsamixer
[*]Installing puvacontrol and playing with the settings there
[/LIST]

So far nothing helps... Does anyone have a clue?

---

### Post by Yellow Pasque on 2013-07-05
Try the latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
If that deosn't work, file a bug:
```
ubuntu-bug sound
```

---

### Post by bug80 on 2013-07-05
Installing the new driver did not help unfortunately.

Before I file an official bug report, is there nothing else I could try?

---

### Post by Yellow Pasque on 2013-07-05
The problem sounds like an issue with amplifier or EAPD pin, which is something that would need to be fixed at the driver level. If you're familiar with these things, you can get the hda-analyzer tool in the snd-hda-tools package here: [https://launchpad.net/~diwic/+archive/hda](https://launchpad.net/~diwic/+archive/hda)
Oh, and I gave you the wrong command before. The command is:
```
ubuntu-bug audio
```

---

### Post by bug80 on 2013-07-05
Thanks for your replies. I installed the tool, but I am a bit hesitant just using trial-and-error with PIN settings here.

I filed a bug report instead: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1198202](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1198202)

---

### Post by bug80 on 2013-07-11
OK, thanks to someone in that bug thread, I got the following work-around:

* Start hda_analyzer
* In Node 0x14, untick the label "OUT"
* Exit hda_analyzer
* Reboot

That solved the volume issue for me!

---

