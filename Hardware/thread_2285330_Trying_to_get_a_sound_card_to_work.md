---
title: "Trying to get a sound card to work"
date: 2015-07-04
forum: Hardware
---

### Post by micromachine on 2015-07-04
I've installed a PCI Soundcard, and it seems like Ubuntu is recognizing it. It shows up in the bios under PCI, I'm able to see it in alsamixer, everything is unmuted and turned up, I can also see the VU meter moving in the Pulseaudio controls when the card is selected and music is playing. So everything indicates that it's working but I can hear nothing out of the speakers.  I posted this over at askubuntu and tried a few things with no success. [http://askubuntu.com/questions/644555/pci-soundcard-to-function#](http://askubuntu.com/questions/644555/pci-soundcard-to-function#)

I'm using Ubuntu 14.04, on a Dell optiplex 745, and the card is an ICEnsemble ICE 1724. 

[IMG]http://imgur.com/6X2lVVj.jpg[/IMG]
[img]http://imgur.com/3oSBzBD.jpg[/img]
[IMG]http://imgur.com/qtvL0i1.jpg[/IMG]

---

### Post by dino99 on 2015-07-05
Actual pulseaudio is very sensitive, and needs:
- jacks plugged into the good support (same color)
- then from 'volume control' select first the 'configuartion' tab then the 'output devices' to set the good settings

---

### Post by micromachine on 2015-07-05
This is what I have set for configuration and output devices
[IMG]http://i.imgur.com/xFOGd4X.png[/IMG]
[IMG]http://i.imgur.com/mmD1NiX.png[/IMG]

---

### Post by tgalati4 on 2015-07-05
Envy24 soundchips are tricky to set up.  They need patches otherwise you get no sound.  Patches are simply connecting inputs to outputs.

Install and run *mudita24* then click on the patches tab and start pressing buttons.

```
sudo apt-get install mudita24
mudita24
```

When you get a working configuration, save it as a "Profile" then make that "Profile" the default configuration.

---

### Post by micromachine on 2015-07-05
I tried this and got the message "no ice1712 cards found"

---

### Post by micromachine on 2015-07-05
> **tgalati4 said:**
> Envy24 soundchips are tricky to set up.  They need patches otherwise you get no sound.  Patches are simply connecting inputs to outputs.

Install and run *mudita24* then click on the patches tab and start pressing buttons.

```
sudo apt-get install mudita24
mudita24
```

When you get a working configuration, save it as a "Profile" then make that "Profile" the default configuration.


I tried this and got the message "no ice1712 cards found"

---

### Post by tgalati4 on 2015-07-05
Yes, you have an ICE1724 card, not an ICE1712 card.  What does the pull-down list of  Profiles show in the Volume-->Configuration show?  You need to be able to select a configuration (profile) that connects the PCM channels (1 and 2) with output channels (1 and 2).  I don't know how to create that configuration file for an ICE1724, but *mudita24* performed that function for older cards.

These are the switches that you can play with for your sound module:

> tgalati4@Mint17 ~ $ modinfo snd_ice1724
filename:       /lib/modules/3.13.0-24-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
license:        GPL
description:    VIA ICEnsemble ICE1724/1720 (Envy24HT/PT)
author:         Jaroslav Kysela <perex@perex.cz>
srcversion:     13668DA01D5539A51E942EC
alias:          pci:v00001412d00001724sv*sd*bc*sc*i*
depends:        snd,snd-ac97-codec,snd-pcm,snd-i2c,snd-ice17xx-ak4xxx,snd-ak4113,snd-rawmidi,snd-pt2258,snd-ak4xxx-adda,snd-ak4114
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512
parm:           index:Index value for ICE1724 soundcard. (array of int)
parm:           id:ID string for ICE1724 soundcard. (array of charp)
parm:           enable:Enable ICE1724 soundcard. (array of bool)
parm:           model:Use the given board model. (array of charp)


---

