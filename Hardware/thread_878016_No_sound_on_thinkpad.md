---
title: "No sound on thinkpad"
date: 2008-08-02
forum: Hardware
---

### Post by remifrommontpellier on 2008-08-02
Hi everyone, 

I'm having reccuring sound problem with an IBM thinkpad T40. I bought it reconditioned a year ago and installed ubuntu. I have never been able to get the sound to work. In it's present setup, i have:

# downloaded and installed the latest alsa 1.0.17
# check "audio setting management (alsa)" in services,
# unmuted all except external amplifier in alsa mixer - and saved it
# added the line "options snd-intel8x0 ac97_quirk=3" in /etc/modprobe.d/alsa-base. This tip was given in [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) for Intel 8x0 soundcard.

Still nothing! Before formating the all hard drive and re-installing ubuntu (something i'd never had to do in 3 years of ubuntu), i'd like to ask on the forum if there's something i haven't tried. I'd also like to hear if kubuntu would give me working sound on the T40?

Here are the output of various commands on my system:

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


~$ lspci -v
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: IBM ThinkPad T41
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
	Memory at c0000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>


~$ sudo modprobe snd-intel8x0

=> no error message... But still no sound:(

---

### Post by remifrommontpellier on 2008-08-04
Well, no progress but it seems that a similar problem exist with ibmx31 as described on this thread:

[http://ubuntuforums.org/showthread.php?t=865060](http://ubuntuforums.org/showthread.php?t=865060)

it doesn't sound good (pun unintended) for getting any sound on these thinkpads...

---

### Post by dzisler on 2008-08-04
I too had a Think Pad 600, could get everything to work great EXCEPT no sound...never. I never needed sound so it was not a big concern, but I did try for some time. Ubuntu worked  great( other than the no sound problem) until the laptop just quit working.

---

