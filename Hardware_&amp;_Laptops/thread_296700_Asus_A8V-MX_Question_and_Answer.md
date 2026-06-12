---
title: "Asus A8V-MX Question and Answer"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by colhom on 2006-11-10
The good first-I have a Asus A8V-MX 939 motherboard, and when I first installed grub on it I wasn't able to boot of my SATA HD when I had a second IDE one plugged in. Turns out this was what the Hardware list said I would encounter. The fix-If you plug in your second hard drive, start up and enter the setup and change your primary boot hard drive to the SATA (It defaults to the IDE) it will boot off the SATA. I don't know if this works for dapper or badger, since I've only tried this on Edgy. 

The bad-I am still unable to figure out how to get the integrated VIA vt82xx integrated sound card to work. Its one of those three jack deals, where the mic and line in jack need to work as rear and center out jacks for surround sound. As of now, I am only able to get 2.1, b/c the two rear and center speakers won't work. Ideas?

---

### Post by Patrick Dixon on 2007-01-27
In answer to your problem, in alsamixer, edit, preferences, there are a couple of options realting to surround sound.  If you enable them, you should then be able to check & change the settings, and that may give you what you're looking for.

However, I too have a A8V-MX and I can't get the sound to work at all!

It seems to find and load the right drivers, but even after playing with all the alsamixer settings, I still can't get any sound.

Suggestions gratefully received.

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8251 [VIA 8251], device 0: VIA 8251 [VIA 8251]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8251 [VIA 8251], device 1: VIA 8251 [VIA 8251]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# lspci -v:
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 70)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b9
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at d400 [size=256]
        Capabilities: [c0] Power Management version 2

# tail -2 /proc/asound/oss/sndstat
Mixers:
0: Realtek ALC655 rev 1

r# asoundconf list
Names of available sound cards:
V8251

---

