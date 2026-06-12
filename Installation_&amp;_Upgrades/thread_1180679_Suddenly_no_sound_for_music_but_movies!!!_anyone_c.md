---
title: "Suddenly no sound for music but movies!!! anyone can help??"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by MacUsers on 2009-06-07
Greetings guys, help me please!!! 

I've never seen this rather unusual thing before. As the title says, I can hear/play sound when I play back movies but there is no sound when I try to play some music (mp3 or m4a etc.). It was working just fine for everything and suddenly just stopped for the music. I checked the alsamixer and it's fine there (remember, the sound works for movies). I tried with VLC and XBMC; get the very same result. I'm totally confused. Can any one pls help? Friends are coming over to see my new system and now I don't have sound for them. I really very much appreciate if any one can help me with some clue(s).

Thanks in advance. Cheers!!!

---

### Post by kiridude on 2009-06-07
that sounds quite strange. Are you playing your movies and mp3's with the same player - both with VLC?

---

### Post by MacUsers on 2009-06-07
Yeah, vlc and also with xbmc, give me the same result. Movies are plying from the HDD so do the mp3 and other formats. Actually, there is no sound at all but sound just comes back when I play movies. Just tried with disks - DVD movies are justfine but not thr audio CDs. Don't know what to do. Cheers!!!

---

### Post by kiridude on 2009-06-07
try fiddling with system > preferences > sound > devices.  Under "music and movies" mine is on "autodetect," but if that doesn't work with your setup, try something else.

What version of Ubuntu r u using?

---

### Post by MacUsers on 2009-06-07
It's v9.0.4, 64-bit Mythbuntu. 
I don't actually have "system > preferences > sound > devices" and I yet to get familiar with Ubuntu system (being a RedHat user), so don't know where else to look. But below some console out-put.

**lspci with hex-dump**:
```
Slot:   00:1b.0
Class:  Audio device
Vendor: Intel Corporation
Device: 82801JI (ICH10 Family) HD Audio Controller
Flags:               bus master, fast devsel, latency 0, IRQ 22
Memory at fe8f4000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-int
SVendor:        ASUSTeK Computer Inc.
SDevice:        Device 82fe
00: 86 80 3e 3a 06 00 10 00 00 00 03 04 08 00 00 00
10: 04 40 8f fe 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 fe 82
30: 00 00 00 00 50 00 00 00 00 00 00 00 03 01 00 00
```[B]
aplay -l: [/B]
```
** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```but I get error, if I try to pay something using aplay:
```
# aplay -Dplughw:X,0 -fcd Chiquitita.mp3
ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
aplay: main:608: audio open error: No such device
```I'm using digital out (S/PDIF). cheers!!!

---

### Post by kiridude on 2009-06-07
Sorry, I did not notice the Mythbuntu tag, I do not know much about that. There is a Mythbuntu section, however, here in the forums where you'll probably find more help. 

You can try running: xfce4-mixer from a terminal to access your sound settings.

---

### Post by VoltRabbit on 2009-06-07
I blame it on being the 64 bit version. Then again, I know very little about linux, but if I learned anything from windows, 64 bit = pain-in-the-ankle.

---

### Post by MacUsers on 2009-06-07
Hi VoltRabbit,
It's juat a bit better then Windows when it comes to 64-bit platform but nothing compare to the 32-bit, indeed. 

Anyway, I've get it fixed (with help from XBMC forum) and it appears to be a stupid ALSA bug. It's reported to be happened sometimes, if the application crashes (or the process is killed for any reason) whilst watching movie that has AC3 or some sort of digital audio. There are several ways to fix that, I believe, so far I know three of them and the first one worked for me. Form a console window

**Option 1: **
```
/usr/bin/ieset on
```[B]
Option 2:[/B]
```
echo "pcm.!default spdif" > ~/.asoundrc
speaker-test -c 2
```If you should hear the sound and if so, you are good to go. Delete the .asoundrc file from the home directory and restart.

**Option 3:**
```
cat /dev/urandom | ac3dec -R
```I haven't tested this but it reported to worked for some people.

Hope it helps, those who have same problem as me. Cheers!!!

---

