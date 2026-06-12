---
title: "Sound comes and goes"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by KLineD on 2006-08-15
Ok, I'm lost with this one.

I recently installed Dapper in a Gateway laptop. Everything is fine I just hope I could make the battery last longer but I really don't have a comparision point since I deleted WinXP as soon as I got my hands in this new laptop.

Anyway the main problem here is the sound. Sometimes when I restart the machine, sound works fine and I hear the drums when gdm starts. But most frequently I can't hear anything.

The sound card I believe is detected fine. Right now I can't hear anything, everything is turned all the way up (using alsamixer) and I think the right modules are being loaded up. The following is the output of lsmod | grep snd:

> snd_hda_intel          20468  1
snd_hda_codec         163088  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm

My card is HDA Intel and the soundchip is a Sigmatel. One thing I noticed is that aplay -l lists one card:

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And the volume control applet lists two devices, HDA Intel (ALSA) and Sigmatel ID 7634 (OSS Mixer) and both have the volume all the way up.

I don't know if the definitive sound guide here in the forums apply to me because my card seems to be correctly detected and sometimes it works allright as long as I don't reboot the machine.

Anyone got any idea of what to do?

Thanks a lot.

---

### Post by NTolerance on 2006-08-17
I have this problem as well.  I just did a fresh install of Kubuntu 6.06.1.  As of 2 days ago I had a fully updated Ubuntu 6.06 install that didn't have this issue.  I was even running the same kernel version on both installs - 2.6.15-26-686.

---

### Post by KLineD on 2006-08-18
Well it seems here that the sound issue is gone as well. I don't know if it was the recent update (I didn't see any sound related files in there) but I'm getting sound everytime I boot.

I'm still not declaring victory... I'll wait and see.

---

### Post by NTolerance on 2006-08-18
Does headphone detection work?

---

### Post by KLineD on 2006-08-18
Yes it does. As soon as I plug my headphones, speakers mute. That is when my soundcard manages to output sound.

I don't know, maybe it has something to do with power management (i'm guessing here) because today when starting the laptop the battery level was very low and no sound at all. I plugged the AC adapter but still no sound. I'm restarting it to see if sound comes back.

---

### Post by NTolerance on 2006-08-18
I just formatted my root partition and re-installed Kubuntu 6.06.1.  I was hoping to install with plain old 6.06, but the mirror sites have taken it down.  My sound worked until I installed the linux-686-smp kernel.  I really can't accept having to choose between working sound and using both cores of my CPU.  At this point I'm giving up and seeing if the kernel included with Mepis 6 will make my system work.  :sad:

---

### Post by KLineD on 2006-08-18
Hmm.. I have the plain 386 kernel still installed. I'll try booting with it to see if it has any effect with sound.

---

### Post by KLineD on 2006-08-18
> **NTolerance said:**
> I just formatted my root partition and re-installed Kubuntu 6.06.1.  I was hoping to install with plain old 6.06, but the mirror sites have taken it down.  My sound worked until I installed the linux-686-smp kernel.  I really can't accept having to choose between working sound and using both cores of my CPU.  At this point I'm giving up and seeing if the kernel included with Mepis 6 will make my system work.  :sad:

Why not try the new Edgy Eft? If you are reinstalling, it's worth a try!

---

### Post by NTolerance on 2006-08-18
Yeah, I might just do that.  Mepis and Ubuntu use the exact same kernel from the same repositories, so I will probably have the same issue with Mepis.  All I really need is the updated kernel/ALSA though, not all the extra stuff that comes with Edgy.  I'll see what happens.

Also, I would be happy to run a 386 kernel with SMP support.  I don't care about SSE3 or whatever, but I have to utilize my 2nd core.  The 686 kernel obviously has lots of issues that the 386 doesn't have.

---

### Post by KLineD on 2006-08-18
Yeah, I don't want either to sacrifice performance over sound, or the other way around. I just wanted to test with the 386 core to see if that was the issue but I'll do it tomorrow.

Ok I tested it. Booted my machine with 686 SMP kernel and sound was not working. Then booted with regular 386 kernel and sound worked fine. Then I booted again with 686 and sound kept working. Overall, sound works with 386 kernel 100% of the time, but only around 70% of the times with 686.

When sound is not working, the soundcard is detected just fine and programs do reproduce media files with no error, just no sound is outputted through the speakers.

---

### Post by NTolerance on 2006-08-21
Well, I formatted yet again and this time I compiled the 2.6.17 kernel as described [here](http://www.ubuntuforums.org/showthread.php?t=217657&highlight=edgy+kernel).  And sound is still broken!  

What a total PITA this has been.  I can only conclude that this problem lies within Ubuntu itself as there are documents about setting up other distros on this laptop and I don't see anything there about these sound problems.  ](*,)

---

### Post by NTolerance on 2006-08-22
I don't know why I keep messing with this, but here's some more info:

1.  I reformatted with Kubuntu 6.06
2.  Installed linux-686-smp kernel
3.  apt-get dist-upgrade
4.  Booted at least 7 times with sound working
5.  Installed ATI fglrx drivers
6.  No sound

---

### Post by NTolerance on 2006-08-22
I just formatted again and installed Mepis 6, the 686 SMP kernel, and the ATI fglrx drivers.  I've rebooted nearly 15 times and my sound is working.  Ubuntu is busted.

---

### Post by KLineD on 2007-03-05
Incredibly I still have the same issue since I first posted this. The only thing that has changed is that now I'm using Edgy Eft with generic kernel.

The thing is, when I boot sometimes I get sound and sometimes I don't. I have tried every combination (boot when on battery power, boot with AC power, muted, unmuted...) I can think of but the problem remains.

alsamixer detects the following info (both when I get sound or when I dont)

> Card: HDA Intel
Chip: SigmaTel ID 7634

The only different thing is when I DO HAVE sound, alsamixer shows MASTER PCM controls. When I DO NOT have sound, alsamixer shows MASTER PCM SPDIF. Obviously I'm 200% sure all controls shown by alsamixer are unmuted and volume is turned up all the way.

Also, when I DO NOT have sound, I get the following:

> cesar@frodo:~$ amixer info
Card default 'Intel'/'HDA Intel at 0xdc400000 irq 66'
  Mixer name    : 'SigmaTel ID 7634'
  Components    : 'HDA:83847634 HDA:10573057'
  Controls      : 5
  Simple ctrls  : 3

cesar@frodo:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdc400000 irq 66

When I DO have sound:

> 
cesar@frodo:~$ amixer info
Card default 'Intel'/'HDA Intel at 0xdc400000 irq 66'
  Mixer name    : 'SigmaTel ID 7634'
  Components    : 'HDA:83847634 HDA:10573057'
  Controls      : 3
  Simple ctrls  : 2

cesar@frodo:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdc400000 irq 66

Is anyone here that can give some pointer to solve this? If I could tell ALSA something like "you know, THIS is the configuration that works, please don't try to autodetect or autoconfigure my soundcard any more. MASTER and PCM are allright, but not SPDIF"

---

### Post by DC@DR on 2007-04-16
I have exactly the same problem with KlineD and I'm stuck at what to do now. Anyone can help us? Thanks :-)

---

### Post by NTolerance on 2007-04-16
KLineD, have you tried updating to the latest release candidate of ALSA?  I remember having some success with it back when I had my laptop.  Apparently the snd_hda_intel stuff is still in fairly early development, so getting the latest ALSA helps a good bit.

I'm thinking that the updated version of ALSA that is included with Feisty may also fix this problem.

---

