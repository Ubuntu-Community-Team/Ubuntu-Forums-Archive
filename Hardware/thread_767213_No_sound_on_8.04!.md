---
title: "No sound on 8.04!"
date: 2008-04-25
forum: Hardware
---

### Post by wildteen88 on 2008-04-25
I have just upgraded Ubuntu from 7.10 to 8.04 by doing a fresh install. 

However I have noticed a problem with 8.04. When 7.10 was installed I had sound supported in the "out of the box" condition. I do not have any sound in 8.04

What has changed in 8.04 that affected the sound?

My System specs are
Intel Core 2 Duo E6400 (Clocked @ 3.0GHz)
ASUS P5B Deluxe
Nvidia GeForce 8800 GTS 320MB

I have tried searching for a SoundMax audio driver which I use for Vista/XP but cant find one for linux. ASUS has a linux audio driver on their site but seems a bit outdated was released sometime in 2006 plus their site is SO bloody slooow!

Thanks for any help.

---

### Post by wildteen88 on 2008-04-26
No one got any suggestions?

I did forget to mention that the soundcard is built into to the mobo and is called
ADI ADI1988B 8-channel High Definition Audio CODEC <-- as mentioned in the mobo manual.

So I presume I need a ADI1988B driver. If I try enabling sound I get the following error:
No Volumne Control GStreamer plugins and/or devices found

---

### Post by wildteen88 on 2008-04-29
Still no suggestions? I tried recompiling the ALSA driver for my chipset Intel8x0 hoping my sound would work. No joy :(

I run through the instructions [here](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0). Everything installs/compiles fine and get no errors during the process.

However when I run the following command:
**alsamixer**
I get the following error:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

I may downgrade to 7.10 instead tomorrow when I get back from work.

---

### Post by gantellus on 2008-05-03
Also no sound on P5B Plus, Ubuntu 8.04

```
mihail@mihail-desktop:~$ alsamixer
ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory
mihail@mihail-desktop:~$ 


```

---

### Post by fuwkej on 2008-05-03
I have the same issue as well.

---

### Post by WildeBeest on 2008-05-03
So do I.

---

### Post by jvilla1983 on 2008-05-03
Have you tried switching the audio driver that you're using from Alsa to OSS? Sometimes when dealing with sound issues I've switched around from different sound drivers just to see if there are any problems. Also, you mentioned that it DID work in a previous version of Ubuntu.. Did you try creating a CD of the previous version and seeing what the settings are on the liveCD distro? maybe that could help you shed some light as to why its not working.

Just a few ideas, I guess that's what I would try first.

---

### Post by Zorael on 2008-05-03
Is this relevant?

[http://ubuntuforums.org/showthread.php?t=287814](http://ubuntuforums.org/showthread.php?t=287814)

---

### Post by magicsmoke on 2008-05-03
I created a thread on this last night, with no replies yet...

My system specs are close to yours, except my video card is a bit older.
I have the ASUS P5B-Plus, using the on-board sound.

This system had no problems with sound in previous Ubuntu releases.  Not sure what the problem is.

---

### Post by toastrbot on 2008-06-14
Try disabling ACPI in your BIOS. Not an ideal solution, but it seems to get sound working.

---

