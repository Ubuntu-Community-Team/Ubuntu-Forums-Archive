---
title: "No Sound - Minimal Jaunty Installation"
date: 2009-05-30
forum: Hardware
---

### Post by tribole on 2009-05-30
I switched from a full installation of Jaunty to a minimal installation together with xfce and lost all sound. I get the following error when booting:

[   11.513092] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   11.513145] ali mixer 1 creating error.

When I run alsamixer (making sure to unmute) it gives the following information:

Card: ALI 5451
Chip: Analog Devices AD1981B

Running lspci gives:

00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
        Subsystem: Sony Corporation Device 8158
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 8800 [size=256]
        Memory at f0401000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ALI 5451
        Kernel modules: snd-ali5451

My computer is a Sony Vaio pcg-fr415s laptop. Any advice would be much appreciated!

---

### Post by chenson13 on 2009-06-09
Exact same issue. Anyone? Bump?

I installed gnome using the following reference. Performance for everything is great. Except audio....
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by tribole on 2009-06-09
I got tired searching the internet for solutions, finding hundreds of people with similar problems but no solutions that worked. In the end I decided to install Intrepid Ibex instead (again the minimal installation) and all the sound came back. I still get the "AC'97 1 access is not valid" error when booting up so that obviously wasn't the problem. Ibex uses version 1.0.17 of alsa whereas Jaunty uses version 1.0.18. Maybe that has something to do with it? Good luck!

---

### Post by chenson13 on 2009-06-11
That sucks. Meaning - I am sure there is a simple answer for this. I really like the minimal install and then adding everything I want afterwards myself. I'll keep digging around as it's not exactly an urgent issue. If I find something, I'll put it on this thread for you. Thanks for responding...

---

### Post by tribole on 2009-06-11
Thanks, I'd be very interested if you find anything. I really like the minimal install as well, makes my 6 year old computer feel like new!

---

### Post by diviaki on 2009-06-16
Had same problem while streamlining a desktop jaunty installation.
This helped to solve problem: [http://ubuntuforums.org/showthread.php?t=1176380](http://ubuntuforums.org/showthread.php?t=1176380)
Basicly now I have alsa-utils and pulseaudio sound related packages installed.

---

### Post by Icebear on 2009-07-23
A bit late but I had the same problem

By chance I got it to work I installed alsa-base and the rest what came with it.

Then I was trying to get what the sound card alsamixer was  trying to read and I typed

alasmixer -c0 in the terminal 
and the mixer came :D

I do not know why but from there I pressed m (to turn the mute off) on the master and the pcm volumes and the my sound worked.

I can not remember this time of installing if I evan added the audio group thing.

---

