---
title: "[Sound] Sound problem on ASUS A8JR"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by darktears on 2007-04-13
Hello all,


I have a little problem with my sound card on my new laptop (model was in store in january 2007 ASUS A8JR). I explain :

I use Kubuntu with feisty (but the same problem was on eidgy and dapper) and my sound card is crazy : we can hear a little sound on the left speaker and on the right speaker a big noise (in headphone it's the same thing).

I search on the web and i see that HDA intel is a recurrent problem...I try lot of solution like add option line in modprobe.d/options : options snd_hda_intel model=LOT (Lot Of Things :D) but no change...Same noise...

My last manipulation was to download latest ALSA driver and utilities (1.0.14rc3) and install it...Installation was good when i open ALSA mixer it's the new version...But same thing big noise...

My card is hda intel ad198x
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]

I know that there are lot of solutions in the web but i try lot of things and i'm deseperate (it's my laptop for working on KDE4) :(

Thank you so much...

darktears

---

### Post by hardyn on 2007-04-13
does it work in windows?

I have personally had-it with Asus notebooks... i had the audio card replaced a few times in my last (pun intended) Asus notebook.

---

### Post by darktears on 2007-04-13
Work fine on windows (no noise)

---

### Post by drummingpariah on 2007-04-18
My a8jm also works great in Windows, and on the old (2.6.20-12) kernel still.  I've tried all sorts of funky configs, like alsa/oss/analog mixers on various settings, but no dice.  

Do we have the same device and driver?

lspci:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by iLoVe.cF- on 2007-04-19
Hi.

This is just noise/disort issue, try pulling down the standard volume abit.. you might be able to do it in the driver.

by the way..

mine got int. cd-player that can be used without startin the laptop.

Quality is excellent, start it in either windows or linux..ohh.. disort/noise :S

IT MAY come from the charger.. try and listen when plugging OUT the AC adapter.

do you get noise my moving a usb mice. ?

do you get noise when GPU/CPU/HDD works.

Test it out.

---

### Post by drummingpariah on 2007-04-19
I forgot to mention that I have no sound whatsoever, not funky sound.  Still working on a cure, re-compiled ALSA,used OSS, set up for Analog output.  Not sure where the problem is, but sound is also dead on the old kernel, which worked pre-update.

---

### Post by dalejefferson on 2007-04-19
Bug already found and fixed, just waiting for Ubuntu to push out a new kernel update (hope its not to long)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105582](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105582)

---

### Post by drummingpariah on 2007-04-19
superb!

... now to just figure out that temporary fix, what it is, and how I use it.  working on it.

---

### Post by dalejefferson on 2007-04-19
> **drummingpariah said:**
> superb!

... now to just figure out that temporary fix, what it is, and how I use it.  working on it.

Very bad fix is to install Xen kernel you gain sound but loose restricted drivers?
I've posted a bug about the lack of restricted drivers with xen

sudo apt-get install ubuntu-xen-desktop

and reboot

---

### Post by dalejefferson on 2007-04-19
Much better fix :KS 

```
cd /lib/modules/2.6.20-15-generic/kernel/sound/pci/hda/

sudo rm *

sudo wget http://adhd.irule.net/~crimsun/snd-hda-codec.ko

sudo wget http://adhd.irule.net/~crimsun/snd-hda-intel.ko

Reboot

```

Sound works great :)

---

### Post by tearaway_Tea on 2007-04-22
2dalejefferson

Thank you match. This solution fixed my problems with sound on ASUS A8Hjc with AD198x Analog device.

---

### Post by drummingpariah on 2007-04-22
I haven't had a chance to test it, hopefully I can try it out tonight.  I'll update with results.

---

### Post by maple03 on 2007-05-17
Asus a8jn. I've downloaded those files. But now another problem appeared. Only right channel works. But in the alsamixer both channels are active. And, besides, when I change the volume, sound disappears at all.

Does anyone knows how to help me? )

---

### Post by drummingpariah on 2007-05-22
> **maple03 said:**
> Asus a8jn. I've downloaded those files. But now another problem appeared. Only right channel works. But in the alsamixer both channels are active. And, besides, when I change the volume, sound disappears at all.

Does anyone knows how to help me? )

It sounds like you may have a different mixer running (esd, maybe) that is running sound to alsamixer.  

By the way, the download did fix my sound problem.  Listening to Avenged at the moment on *-15 kernel

---

### Post by Laeg on 2007-08-05
@maple03: Had exactly the same problem. I downloaded the modules described above but when I wanted to change the volume everything muted.

Found a great Guide though:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

After that, everything worked just fine and I don't even know if it's really necessary to use the special modules.

So long

---

