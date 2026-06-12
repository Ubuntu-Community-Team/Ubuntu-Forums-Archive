---
title: "[SOLVED] Sound, is my card broken?"
date: 2008-11-27
forum: General Help
---

### Post by jon.mithe on 2008-11-27
Hi,

I've never had trouble in ubuntu with my soundcard.  I have a bog standard dell core duo with an intel mobo + integrated soundcard.  Past couple of years its been fine, last week its not.

For a couple of days I would get sound sounding slightly odd, and within in a minute or two listening to music, it would just get quieter and quieter till it faded to nothing. No system sounds were audible etc.

For the last couple of days my sound has just gone.  Where the ubuntu theme intro is or when I play music, I just get clicks from the speakers.  Clicks are very quick and sharp, they sound of the electrical sort (sorta like what mobile phones can do) but have no regular pattern and are ~1 a second if that.

Dell PC's have a socket infront where headphones go to, other day moved from my chair and yanked the headpone socket out quite sharply (no the soket in the pc, just the headphones).  Headphones do work, an I also get the problem through the speakers on the back.

aplay -l 

```

card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v 

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 01dd
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dffdc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```


It would seem to suggest my card is installed and ubuntu recognises and tries to play sounds but something is screwing it up.

I thought I may have damaged the socket causing some sort of interferance or something, so tried unplugging the mini breakout panel its on from the mobo.  But dell in there infinite wisdom have also put the power button etc on it as well all through the 1 parallel connection type cable, so my pc didnt turn on when I tried this obviously :P. 


Oddly enough I've been having some focus issues on my setup (which seemed to have resolved themselves) in this thread, [http://ubuntuforums.org/showthread.php?t=992901](http://ubuntuforums.org/showthread.php?t=992901) . So I am not 100% confident the sound card has packed in or something is screwing around with my sound.

Is my soundcard dead? or are there any more things I can try.  Is there a sudo dpkg-reconfigure type thing I can do to reconfigure / setup the sound?

I'm on a bog standard dell core duo from a couple years ago, up to date version of 8.10 with no thrills (3D effects etc are all off).  Its a work PC so pretty much I just use eclipse / thunderbird.

Thanks for any help,
Jon

---

### Post by jon.mithe on 2008-11-28
Gave up, guessing its broken.  Found a random soundcard in an old desktop server, so pinched that :P

Jon.

---

