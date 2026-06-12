---
title: "No Soundcards found in 9.04"
date: 2009-04-25
forum: Hardware
---

### Post by giddensdb on 2009-04-25
I have an Acer 5515 laptop currently running Ubuntu 9.04 and my sound card worked fine under 8.04 using alsa.  In 8.10 and now in 9.04 aplay -l reports no sound cards found.  

broc@broc-laptop:~$ lsb_release -rd
Description:	Ubuntu 9.04
Release:	9.04

broc@broc-laptop:~$ aplay -l
aplay: device_list:217: no soundcards found...


broc@broc-laptop:~$ lspci -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Gateway 2000 Device 0184
	Flags: bus master, slow devsel, latency 64, IRQ 11
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


Any suggestions?

---

### Post by dlstyley on 2009-04-26
I have the exact same problem after an upgrade from Intrepid (8.10).  Did you upgrade or clean installl?

Did you notice in your mixer settings that the device is listed as follows?

> Playback:  Null Output (PulseAudio mixer)


Anyway, someone in another forum suggested a workaround of setting "Sound Theme" to "No Sounds" and rebooting.  That does work for me, but it sucks because if you reboot without remembering to set your theme to "No Sounds" then your sound is broken again.

---

### Post by giddensdb on 2009-04-29
I did an upgrade as opposed to clean install.  Where are you setting sound theme to no sounds?  System -> Preferences -> Sounds?

My alsamixer won't even open.  When I tried to get the newest alsa drivers I kept getting error messages.  Anyone figured this out?

---

### Post by dlstyley on 2009-04-29
I'm at work at the moment, so I can't tell you for sure...

Note that I fixed this by adding an "options" line in a config file:

> options snd-intel-hda model=acer

it was in /etc/modprobe.d/alsa-base.conf

Here is some info on this...
[http://ubuntuforums.org/showthread.php?p=7167978](http://ubuntuforums.org/showthread.php?p=7167978)

Good luck!

---

### Post by giddensdb on 2009-05-04
I will try that and post back to let you know. Thanks.

---

### Post by giddensdb on 2009-05-05
Still nothing.  I am backing up my home folder and doing a clean install to see if that helps.  I'll post again with any progress or lack of....

---

### Post by giddensdb on 2009-05-05
Clean (re)install proved to be the answer.  After reinstalling my sound card worked immediately.  So did my on board wifi which i had previously been using ndiswrapper to make work.  Thanks to everyone for their ideas.  Hope this helps someone else.

---

