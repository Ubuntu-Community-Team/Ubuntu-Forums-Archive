---
title: "sound only works in headphones"
date: 2011-02-20
forum: Hardware
---

### Post by Dasdre on 2011-02-20
I have Bang & Olufsen ICEpower speakers built-in in my asus N53J, and they refuse to work, when i play anything with sound, it refuses to work as if someone had removed the speakers.
lshw and similar lists my sound card but the sound is not working, it is not hardware muted or similar and the sound does not play in the speakers even when headphones are plugged in, only in the headphones.
Any help would be greatly appreciated.

---

### Post by fjgaude on 2011-02-20
First off, did the speakers ever work correctly?

Second, what does the menus in System, Preferences, Sound show?

---

### Post by gruffyddd on 2011-02-20
Try the usual suggestions, but it may be due to [this]("https://bugs.launchpad.net/ubuntu/+bug/708586") bug. If you can boot into the previous kernel it should tell you for definite if that bug is the cause of your problems.

---

### Post by Dasdre on 2011-02-21
> **fjgaude said:**
> First off, did the speakers ever work correctly?

Second, what does the menus in System, Preferences, Sound show?

1. Yes, in windows they did.

2. I'm using KDE.

> **gruffyddd said:**
> Try the usual suggestions, but it may be due to [this]("https://bugs.launchpad.net/ubuntu/+bug/708586") bug. If you can boot into the previous kernel it should tell you for definite if that bug is the cause of your problems.

How do i do that?

EDIT: 
Nevermind, solved it by changing to windows.
(Officially supported by ASUS)

---

### Post by marcussive on 2011-02-26
Hello, I am new to Linux (1 day). So far so good but... I have this same issue with Ubuntu10.10 - I get sound from headphones but not through speakers. The speakers work fine in Windows 7.

I did most of this: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
and it appears that my sound card is recognized and functioning. Here are my details:

[http://www.alsa-project.org/db/?f=68d2a761bf1990f2e4eefa7479d3011bc2f78672](http://www.alsa-project.org/db/?f=68d2a761bf1990f2e4eefa7479d3011bc2f78672)

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
        Subsystem: ASUSTeK Computer Inc. Device 1113
        Flags: bus master, fast devsel, latency 0, IRQ 48
        Memory at d9c00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel

!!ALSA Version
!!------------
Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23

Codec: Realtek ALC259

I welcome your suggestions!

---

### Post by tep200377 on 2011-03-10
This page worked it out for me!

[http://blog.tersmitten.nl/archives/1082](http://blog.tersmitten.nl/archives/1082)

>  After having some trouble finding the HDD which I wanted to replace by an OCZ Vertex 2 I also had difficulty getting my speakers  to work. The headphones worked fine but no sound from the speakers. After searching for quite some time I finally found the solution:

sudo nano /etc/modprobe.d/alsa-base
options snd-hda-intel model=auto

I also added the ubuntu-audio-dev repository but I’m quite sure this is not what fixed my problem… 

---

