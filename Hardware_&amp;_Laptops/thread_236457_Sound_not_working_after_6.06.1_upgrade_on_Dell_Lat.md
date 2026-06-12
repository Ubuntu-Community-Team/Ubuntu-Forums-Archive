---
title: "Sound not working after 6.06.1 upgrade on Dell Latitude D620"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by andiii on 2006-08-14
Sounddevice is an Intel 82801G ICH7, it was working before I upgraded. Now I tried several things like installing ALSA stuff and following instructions on whatever weird websites to get alsa running. None did work.

XMMS starts playing mp3 without any error msg, I just cant hear anything. System sound won't play as well, so its not an mp3 problem.

Opening the Volume control I can choose from HDA Intel (Alsa mixser) and an OSS mixer, none does any sound...

Anybody got this working?


edit: After a reboot the sound works!? Is this Windows or what? :)
One thing I'm not happy with now: When I plug in headphones it won't mute the speakers.


Here some informations:

laptop:~$ cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xdfebc000 irq 233

laptop:~$ uname -a
Linux aw-laptop 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686 GNU/Linux

alsamixer:
Card: HDA Intel                                                                                               &#9474;&#9474; Chip: SigmaTel STAC9200    

-laptop:~$ lspci | grep Audio
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
      
laptop:~$ dmesg | grep ICH7
(nothing)

laptop:~$ lsmod | grep snd
snd_hda_intel          20468  1
snd_hda_codec         163088  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm

---

### Post by KLineD on 2006-08-15
This seems very similar at what I'm experiencing right now. Look at my post [right here]("http://www.ubuntuforums.org/showthread.php?t=237152"). 

Is sound working fine between reboots?

---

### Post by andiii on 2006-08-15
Well, the sound is working now (not sure why, but happy!)

Only thing that still annoyes me is that the speakers don't mute when I plug in earphone. How can I listen to music at work now? :confused:

---

### Post by KLineD on 2006-08-15
When my soundcard works and I plug my earphones the speakers do mute... weird.

---

### Post by NTolerance on 2006-08-18
What method did you use to upgrade to 6.06.1?

---

### Post by andiii on 2006-08-21
I downloaded ubuntu-6.06.1-alternate-i386.iso (alternate because I have CoreDuo), mounted and then upgraded.

---

### Post by &#12465;&#12452;&#12488; on 2006-08-26
I've had problems with the sound sometimes working and sometimes not, and am pretty tired having to reboot my laptop several times every day to get some sound on here. A new ALSA could probably be the fix, I'd thought, but both times I've tried dist-upgrading to edgy, apt has failed and messed up my whole system, making me format the thing afterwards.

However, no sound means no fun. I run Ubuntu exclusively, so it has to work for all my desired tasks! I installed the alsa-base package from edgy's repositories, and then the sound came back! I have no idea if it was a very good idea to do, though, but it does seem to work without any hiccups so far, so I'm satisfied. The 6.10 upgrade will probably be a good thing for us hda-intel people.

---

### Post by &#12465;&#12452;&#12488; on 2006-08-26
Damn. After a reboot, it'd stopped working again. (;_;)

---

