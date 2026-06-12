---
title: "Stereo Sound on IEC958"
date: 2009-11-24
forum: Hardware
---

### Post by mathis23 on 2009-11-24
Hey there,

I am running Ubuntu server on a Shuttle XPC as a file server and media center. My AV receiver is hooked up to the PC via S/PDIF. I can play AC3 and DTS movies without any error, all 6 channels are transferred to my receiver and are decoded there. What does not work is playing stereo music or videos. My receiver indicates that it receives front audio, aka 2 channels -> stereo. But I don't get any sound. I checked all channels with alsamixer and unmuted them, but still - no sound on stereo files :/
I have no idea what to do now. Any tips?

Some info about my setup:

# Ubuntu Server Karmic 9.10

# uname -a: Linux conquistator 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux

# 00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

# aplay -l
**** List of PLAYBACK Hardware Devices ****
XOpenDisplay() failed
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# cat /proc/asound/cards 
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC650F at irq 17

---

### Post by kridybel on 2009-12-11
Hello,

After testing distro's on an old laptop I decided to go for ubuntu on my main PC. Unfortunately ubuntu 9.10 does not give any sound on my DELL dimension 4600. But in XP it works fine.

Same card as mentioned above.

aplay -l gives:
[INDENT]**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: ICH5 [Intel ICH5], apparaat 0: Intel ICH [Intel ICH5]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: ICH5 [Intel ICH5], apparaat 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0[/INDENT]

lspci -v gives:
[INDENT]00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ee00 [size=256]
	I/O ports at edc0 [size=64]
	Memory at febffa00 (32-bit, non-prefetchable) [size=512]
	Memory at febff900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0[/INDENT]


I have googled around. It seems like a lot of ubuntu users have the no sound problem with the card that is installed in the DELL dimension 4600. Unfortunately I did not find any solution. Things I have tried:

[LIST]
[*]unmute everything in alsamixer
[*]sudo modprobe snd-intel8x0
[*]add snd-intel8x0 to etc/modules
[/LIST]


Any help would be appreciated.
Thanks

---

### Post by kridybel on 2009-12-18
Solved

Installed the gnome alsa mixer:
> sudo apt-get install gnome-alsamixer

Unchecking the headphone jack sense gave me sound.
See attachment for my settings that work.

---

