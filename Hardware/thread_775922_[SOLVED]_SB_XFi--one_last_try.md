---
title: "[SOLVED] SB XFi--one last try"
date: 2008-04-30
forum: Hardware
---

### Post by kwatson512 on 2008-04-30
Warning:  possible stupid newbie question!

Ubuntu 8.04 Hardy Heron
Dell XPS 400
Intel Pentium D 2.80 GHz
Creative SB X-Fi sound card
Dual boot with WinXP (Windows installed first)

This is my third linux installation, and I've begun to get comfortable with CLI (but am nowhere near proficient).  This was a flawless installation except for the sound card and scanner.  (I'll deal with the scanner later.)  Seems like lots of folks have had trouble with this sound card.  

```
aplay -l
```
results in ```
aplay: device_list:221: no soundcard found...
```

```
lspci -v
``` shows the hardware, but says no driver is installed.

I've compiled and installed the alsa-base, including tools and utilities, but I forgot to install build-essential.  I've also tried installing the beta driver from Creative (XFiDrv_Linux_US-1.18) but I believe the installer they provide is flawed.  It's proprietary and includes imbedded license agreements that you have to say "Yes" to a couple of times or the process stops.

Then I tried using the OSS driver (oss-linux_v4.0-1015_i386.deb).

I discovered a thread [here ]("http://ubuntuforums.org/showthread.php?t=571656") that may work.

My question is whether I need to purge the alsa-base, utilities, and tools before installing build-essential (and then re-installing the alsa-base), or can I just go through the process at the link?

Thanks,
Ken

---

### Post by kwatson512 on 2008-04-30
Well, I went through every process I think exists regarding the SB X-Fi driver, and nothing worked.  NO sound!  I have a good alsa-base now, so should be able to support sound cards that have Linux drivers.

So what I want to do now is go out and buy another sound card.  I would really appreciate any suggestions.  The [ALSA sound card matrix]("http://www.alsa-project.org/main/index.php/Matrix:Main") lists way too many for me to decide easily, and the ubuntu [hardware compatibility list]("http://ubuntuforums.org/showthread.php?t=361236") isn't organized by sound cards.  

I'm looking for a PCI sound card that will support 2.1 speakers and work with Ubuntu with no (or a minimum) of fuss).

Any recommendations?

Thanks,
Ken

---

### Post by Ripfox on 2008-04-30
> **kwatson512 said:**
> Well, I went through every process I think exists regarding the SB X-Fi driver, and nothing worked.  NO sound!  I have a good alsa-base now, so should be able to support sound cards that have Linux drivers.

So what I want to do now is go out and buy another sound card.  I would really appreciate any suggestions.  The [ALSA sound card matrix]("http://www.alsa-project.org/main/index.php/Matrix:Main") lists way too many for me to decide easily, and the ubuntu [hardware compatibility list]("http://ubuntuforums.org/showthread.php?t=361236") isn't organized by sound cards.  

I'm looking for a PCI sound card that will support 2.1 speakers and work with Ubuntu with no (or a minimum) of fuss).

Any recommendations?

Thanks,
Ken

I have a SoundBlaster 16 in my basement I'll sell ya!!

---

### Post by kwatson512 on 2008-05-01
Actually, I have additional requirements for a sound card:
- 5.1 speaker capability
- front mic/line in
- front headphone out
- onboard synth (I write and arrange music)
- compatible with *both* ubuntu and Windows XP Media Center Edition
- decent specs (S/N ratio, freq range)

Any pointers would be much appreciated.

Thanks

---

### Post by Sirron on 2008-05-01
I suspect the Creative Audigy SE would suit you, I used to have one (before I "Upgraded" to X-fi ^^) and I'm sure it worked on both ubuntu and Vista.

---

### Post by kwatson512 on 2008-05-01
You say you upgraded to X-Fi.  Did you get it to work in Ubuntu?

---

### Post by Sirron on 2008-05-04
No, not yet. I'm using my motherboard's onboard sound.

What I do is have my headphones connected to the onboard sound, and speakers connected to the X-fi. It's pretty straightforward to switch between them on vista and saves messing with cables. Obviously, I can't use my speakers at the moment.

---

### Post by kwatson512 on 2008-12-17
I finally got my XFi card to work!  OSS has a new set of drivers and instructions [here]("http://www.4front-tech.com/download.cgi").

---

### Post by kwatson512 on 2008-12-17
I finally got my XFi card to work!  OSS has a new set of drivers and instructions [here]("http://www.4front-tech.com/download.cgi").

---

### Post by Smeags on 2008-12-17
kwatson, 

Great to hear you got your X-Fi working!  I also have an X-Fi and I'm looking to install Ubuntu once I (hopefully) get a new hard drive for Christmas.  I noticed that when running the live CD on my system I had no sound.  I'll have to follow the link you posted and give it a shot once I get to that point.

I have basically no linux experience so you may see me posting some questions on here in the near future.

---

