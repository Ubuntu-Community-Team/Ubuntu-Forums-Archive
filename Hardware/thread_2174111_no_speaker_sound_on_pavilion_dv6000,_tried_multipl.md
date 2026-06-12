---
title: "no speaker sound on pavilion dv6000, tried multiple fixes"
date: 2013-09-12
forum: Hardware
---

### Post by b00mzi11a on 2013-09-12
hi all,

my 'new' laptop is an HP Pavilion DV6000.  I just loaded 12.04 on it and updated.

My problem is no sound coming from the speakers.  I can get headphone sound no problem and I haven't tried the digital output.  I have no way of verifying that its an OS related issue and not a hardware related issue without doing something crazy like loading windohs.

So far I've attempted to fix the problem by typing alsamixer into terminal:  master volume was at zero, fixed that but no effect on speaker output

I've also edited [COLOR=#000000][FONT=Ubuntu Mono]alsa-base.conf[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] and added the line [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]options snd-hda-intel model=dell-m4-3 enable_msi=1[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]   
 
When that didn't work I tried different values instead of 'dell-m4-3' such as auto and hp.

When that had no effect I also added the line [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]alias snd-card-0 snd-hda-intel[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] before the 'options' line stated above.
 
still no effect. 
 
Here are the sources for my above attempts:
[/FONT][/COLOR][http://thisismyeye.blogspot.com/2012/06/no-sound-on-ubuntu-1204-after-upgrading.html](http://thisismyeye.blogspot.com/2012/06/no-sound-on-ubuntu-1204-after-upgrading.html)
[http://ohioloco.ubuntuforums.org/showthread.php?p=9664708](http://ohioloco.ubuntuforums.org/showthread.php?p=9664708)[COLOR=#000000][FONT=Ubuntu Mono] 

I assume you can probably tell from the above post that I'm a copy/paste ninja, not an ubuntu guru.  I've run out of articles to copy/paste from!  Can anyone help?  I'd be happy to post any terminal outputs if you tell me what to input.

here's the result for aplay -l

[/FONT][/COLOR]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Yellow Pasque on 2013-09-13
More info please: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by b00mzi11a on 2013-09-15
Sure, here goes:

[http://www.alsa-project.org/db/?f=80e432bb2100a7b4a99a215fad125978ab34cb62](http://www.alsa-project.org/db/?f=80e432bb2100a7b4a99a215fad125978ab34cb62)

---

### Post by Yellow Pasque on 2013-09-15
First of all, remove your customization by taking out that line you added:
```
snd-hda-intel: model=dell-m4-3 enable_msi=1
```

Next, either install the lts-raring kernel, or just update the sound module if you're happy with your current kernel:
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by b00mzi11a on 2013-09-19
I removed the added lines and loaded the alsa drivers as explained in the link.  Still no sound.  

The only change related to the problem is that now the lit 'mute' button on my keyboard is always orange.  If I press the button it turns blue for a couple seconds and then turns back to orange.  The on-screen volume control isn't muted, and if I click on sound settings the keyboard button turns blue but there's still no sound when I do a sound test.

---

### Post by Yellow Pasque on 2013-09-19
If it's not too much trouble, can you get the updated info?: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
I want to make sure this has been updated:
```
Driver version:     1.0.24
```

---

### Post by b00mzi11a on 2013-09-22
[COLOR=#222222][FONT=Verdana]The driver version still shows 1.0.24   [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I think I know the score.  I followed the instructions at [/FONT][/COLOR][FONT=Verdana][https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) [/FONT][COLOR=#222222][FONT=Verdana]and installed [/FONT][/COLOR]oem-audio-hda-daily-dkms [COLOR=#222222][FONT=Verdana]butI think you wanted me to install [/FONT][/COLOR]oem-audio-hda-daily-lts-raring-dkms?

thanks for all your help btw.  I love the OS for many reasons but the community support is what really makes it great.

---

### Post by Yellow Pasque on 2013-09-22
You're still using the original precise kernel (3.2.x) so oem-audio-hda-daily-dkms was correct (not sure why it didn't install).

---

