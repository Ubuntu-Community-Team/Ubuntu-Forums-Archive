---
title: "Toggle Keys do not sound"
date: 2008-11-24
forum: General Help
---

### Post by t.septekin on 2008-11-24
Hello all,

Problem: Toggle keys do not sound

Device: Sony Vaio VGN-FZ21-M laptop

Operating System: Ubuntu 8.04 or Ubuntu 7.10

Audio device: Intel Corporation 82801H (ICH8 Family)

Its driver: HDA Intel latency=0 module=snd_hda_intel

Settings: System > Preferences > Assistive Technologies > Enable Assistive Technologies "ticked"
	Keyboard Accessibility > Accessibility > Notifications Beep when a toggle key is pressed "ticked"

Volume Control: HDA Intel (Alsa mixer)
	Playback window has two controls, Master and PCM.
	Both are at maximum, both speaker icons enabled

System > Preferences > Sound > Sounds
	All sound when tested

Log out, log in, system start all produce their respective sounds.

At terminal, however, <echo -e "\a"> does not give a sound.

In my other machine, an HP Pavilion zv6245 running Hardy, all is well.

The problem is particularly annoying in Vaio as its caps lock indicator is a tiny led, located well away from the key. And I am a two-thumb typer.

It would appear that this problem is related to Sony Vaio. By the way, the speakers do cut out when I insert headphones: after I modified the alsa-base file (running Hardy but not when running Gutsy!).

I wonder if any Vaio user has experienced the same and succeeded in fixing it?

Thanks to all who read this.

teoman

---

