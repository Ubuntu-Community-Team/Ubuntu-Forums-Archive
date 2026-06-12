---
title: "Internal microphone does not work in Asus 1001px"
date: 2010-12-24
forum: Hardware
---

### Post by irpsit on 2010-12-24
Hello all, I have a Asus eeePC 1001px, and a fresh Maverick install. I have Alsa 1.0.23 (as seen by cat /proc/asound/version)

My Internal microphone does not work out of the box.

I tried every solution without result.

First I know about setting the microphone channel only to left, or only to right, because the microphone is a mono device. So, I always choose these settings (in Alsamixer or pavucontrol).

Then, I tried editing alsa-base.conf file with different suggested options (one by one, after rebooting):
options snd-hda-intel model=auto
options snd-hda-intel model=fujitsu
options snd-hda-intel model=lifebook

In all of them, the internal microphone does give any sound.

Later, I tried to install HDA-Analyser ([link]("http://www.alsa-project.org/main/index.php/HDA_Analyzer")) or also tried the alternative HDA-verb and played with different settings, suggested here ([link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183")), including /usr/local/bin/hda-verb /dev/snd/hwC0D0 0x023 SET_CONNECT_SEL 0x5 and **[COLOR="Red"]nothing still makes the internal microphone work[/COLOR]**!

I am trying this with the gnome-sound-recorder (because I know it's the simplest recorder, and Skype has some additional issues).

Could someone find a solution for this never-ending problem?
I would be very glad for a solution.

---

### Post by Titi on 2011-01-02
same here. pitty, because ubuntu is way faster than windows 7...

---

### Post by yavor1912 on 2011-01-08
I tried almost everything but no result. The solution is to buy a mini microphone from ebay ~ $10.00 USD. Let mi know if you have a better solution
May be to wait till april for the new ubuntu realise 11.04 if the bug will be fixed

---

