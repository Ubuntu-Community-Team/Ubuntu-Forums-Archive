---
title: "How to remove or disable MIDI device w/o disabling audio (snd_ice1712 ; Delta 1010)"
date: 2022-03-08
forum: Hardware
---

### Post by numbstation on 2022-03-08
TLDR: Is it possible to disable, remove, or hide my M-Audio Delta 1010's MIDI interface *without* disabling audio I/O via the same device? If so, how?

Here's my situation:

1. I'm in the process of setting up a refurbished HP Z640 workstation for use as my DAW, to replace an even older machine. Installed my M-Audio Delta 1010 (PCI card w/ rackmount breakout box) yesterday into the computer's only PCI slot.
2. Audio I/O works 100% as far as I can tell.
3. (the problem) Any active MIDI connection immediately causes a crash & hard reset. The computer then shows an error screen in post (928 Fatal PCI error Ues: 0x0) before rebooting normally. All BIOS self-tests pass, nothing I can see in the BIOS settings that would be a problem, and the card shows up as expected via *lspci*, *aplay -l*, etc. Basically, it seems to work fine as long as nothing tries sending/receiving MIDI data.
4. I've tried re-seating the card, turning it on and off again, etc. I have not tried replacing the DB25 cable, but it's on the to-do list.

I have a USB MIDI interface (Roland UM-ONE) that works fine, so I don't *need* MIDI via the Delta 1010. BUT, I use a variety of software that will attempt to connect to a MIDI device as soon as it is selected via dropdown menu, etc... basically, I don't want to an inaccurate mouse click to make my system barf. Would prefer it if alsa & jack just ignored the 1010's MIDI ports altogether, but I still want to use it as an audio I/O device.

Output of* lspci | grep audio*
```
07:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
```

Output of *aplay -l*
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC221 Analog [ALC221 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
(... removed extra HDMI device entries for brevity ...)

card 2: M1010 [M Audio Delta 1010], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

Output of *amidi -l*
```
Dir Device    Name
IO  hw:2,0    M Audio Delta 1010 MIDI
IO  hw:3,0,0  UM-ONE MIDI 1
```

Solutions I *think* might be possible & acceptable, but am not sure how to implement:
1. Force jack or alsa to ignore those MIDI ports, but not the audio ports?
2. Disable the MIDI interface via the driver (eg., some option that can be passed to snd_ice1712)?
3. Something I haven't thought of?

*Note: Posted in "Hardware" since this is fundamentally about a card/slot/driver issue, but if mods think it'd be better in another section, feel free to move!*

---

