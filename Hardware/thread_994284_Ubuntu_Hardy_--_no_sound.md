---
title: "Ubuntu Hardy -- no sound"
date: 2008-11-26
forum: Hardware
---

### Post by NFN Smith on 2008-11-26
I'm having to get sound working on my Ubuntu installation.

The box in question is a desktop machine, where Ubuntu 7.10 was preinstalled, and it's running an AMD64 processor.

When I first started using the box, it was having severe stability problems.  I first moved KDE as the default desktop, then upgraded to 8.04, and since then, I've had no problems with stability.  I don't know if the sound was working before the upgrade, but in the current state, I don't have any sound now.  However, I'm pretty confused about how to get things working -- I've done quite a bit of web searching, but don't have quite enough detail that seems to translate into "what do I do next?".

The sound device that I have is is one that's integrated with the motherboard.  Information that seems to be essential:

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia

Thus, I know that I have an ATI SBx00 Azalia device, and that the device has been detected.  However, when I run something that generates sound (say, the Amarok introduction clip), I see evidence that the sound is being generated, but I'm not hearing anything.

I've run alsamixer, and made sure that there aren't any of the controls there that are set to zero levels, but still not getting anything.

How do I procedd from here?

NFN Smith

---

### Post by markbuntu on 2008-11-26
One stop sound troubleshooting and configuration for hardy:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

There is a bunch of links for hda devices there as well as general troubleshooting and configuration help. Ubuntu 8.04 uses pulseaudio and it is misconfigured in the standard installation/upgrade process.

---

