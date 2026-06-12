---
title: "Can't get headphone jack working in Ubuntu 15.10 ALC668"
date: 2015-10-27
forum: Hardware
---

### Post by ezstyles88 on 2015-10-27
Hello all,
 
 
 As the title says I am having trouble getting the headphone jack to work on my Asus G751-JM running Ubuntu 15.10. When headphones are plugged in, the audio still comes through the built-in speakers. I have been using linux for a good while now but have just recently come back to Ubuntu.
 
 
 As far as what I have tried so far:
 
[LIST]
[*] I have     verified that I do NOT have the jack muted in Alsamixer. 
[*] I have     verified that it is NOT  a hardware fault issue (Headphones work, same     jack works on Windows) 
[*] I have tried     the other jacks on my computer to see if it's a mapping issue (I     think that's the right term :D) 
[*] I have tried     adding ```
options snd-hda-intel model=asus-mode5
``` to my     /etc/modprobe.d/alsa-base.conf as suggested by     [http://ubuntuforums.org/showthread.php?t=2261149](http://ubuntuforums.org/showthread.php?t=2261149)     for a similar G751. And also ```
options snd-hda-intel     model=asus
``` ```
options snd-hda-intel model=auto
``` and     ```
options snd-hda-intel model=laptop
``` with and without     ```
options snd-hda-intel position_fix=1 enable=yes
``` as     suggested by [http://ubuntuforums.org/showthread.php?t=1774627](http://ubuntuforums.org/showthread.php?t=1774627). 
[*] I looked at     [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)     but I don't see a dkms package for Ubuntu 15.10 and I'm hesitant to     try the 15.04.1. 
[*] I have tried     updating the dkms by ppa as suggested in     [http://askubuntu.com/questions/150887/sound-from-both-headphones-and-speakers](http://askubuntu.com/questions/150887/sound-from-both-headphones-and-speakers),     but again, no package for Wily 
[*] I have tried     it from a Live Ubuntu USB and same issue 
[*] I have     checked /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz for     the correct mode to set in alsa-base.conf but it has no option for     ALC668 
[*] I have tried     a different kernel (4.0.1) instead of 4.2.0 
[*] I have gone     through every option on the first page of search results from these     forums for “Headphone jack” as well as all results mentioning     Asus. As well as many other suggestions when searching the same in     Google, most of which had the same suggestions as tried above, or     had outdated information. 
[/LIST]
 
 
 Does anyone have any ideas as to what I should try next? If there is any pertinent information missing I can provide it. Thanks

---

### Post by Yellow Pasque on 2015-10-27
Did you try asus-mode4? [http://www.ingenuitypending.com/asus-rog-g751-and-linux/](http://www.ingenuitypending.com/asus-rog-g751-and-linux/)

If that doesn't work, give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> I have checked /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz for the correct mode to set in alsa-base.conf but it has no option for ALC668
ALC668 is grouped with ALC662. These fixes shouldn't need to be manually applied though. So if you find one that works, report it as a bug on kernel bugzilla.

---

### Post by ezstyles88 on 2015-10-27
No change with asus-mode4. I will try the other options as well and report back

Results of Alsa Info are here: [http://www.alsa-project.org/db/?f=2a467ef47af598c8ef450abf4b42d6d06e494d03](http://www.alsa-project.org/db/?f=2a467ef47af598c8ef450abf4b42d6d06e494d03)

Thank you

*update* I tried with asus-mode1-8 and none of them worked

---

### Post by Yellow Pasque on 2015-10-28
I would suggest filing a bug then (include the link to your alsa info). It looks like your model has a headphone and s/pdif out combination jack.
[https://bugzilla.kernel.org/](https://bugzilla.kernel.org/)

---

### Post by whaddyaknow on 2015-10-28
I had exactly the same problem since yesterdays upgrade from 15.04 to 15.10. After a LOT of trial and error with hdajackretask, different alsa options etc. to no avail.  In the act of desperation I removed hdajackretask patches, my own patches and added:  options snd-hda-intel model=asus-mode5 (its pin settings map headphones to line out [furthest jack input on the right])  and now my headphones work via line out.  No luck on mic though.

---

### Post by ezstyles88 on 2015-10-28
> **Temüjin said:**
> I would suggest filing a bug then (include the link to your alsa info). It looks like your model has a headphone and s/pdif out combination jack.
[https://bugzilla.kernel.org/](https://bugzilla.kernel.org/)

I submitted a bug report and got a reply saying that 
BIOS doesn't seem to pass the proper pin configuration for your headphone jack.
You have to figure out by yourself, e.g. via hdajackretask or such utility, which pin corresponds to which actual I/O

I have installed alsa-tools-gui and am trying a few different options. I will report back with results for anyone else having a similar problem

---

### Post by Yellow Pasque on 2015-10-28
Please link to the bug report.
EDIT: Nvm, I see it: [https://bugzilla.kernel.org/show_bug.cgi?id=106771](https://bugzilla.kernel.org/show_bug.cgi?id=106771)

---

### Post by ezstyles88 on 2015-10-28
Ok so I am having trouble getting anything accomplished with hdajackretask. I attached an image of hdajackretask window. I'm assuming the jack I'm trying to work with is 'Internal SPDIF Out' shown at the bottom, as it is the only spdif jack. Though I would think it would say 'Right side' along with my 'Black Line Out, Right side' and 'Black Mic, right side' as those jacks are right next to my spdif jack. Anyhow, when attempting to override the spdif jack, clicking 'Apply now' first complained "tee: /sys/class/sound/hwC1D0/reconfig: Device or resource busy" though "lsof" and "fuser" both returned nothing. 
Following a post in [this]("https://www.reddit.com/r/linux/comments/17sov5/howto_beats_audio_hp_laptop_speakers_on/") thread for the same issue, running ```
sudo fuser -v /dev/snd/*
``` showed processes running and I killed those however I still get the same error. I read the Documentation for HdaJackRetask that is in the window but it doesn't tell  me much and as I am not experienced or well read on the program I am hesitant to try the Expert options.
I also tried running HdaJackRetask with gksudo, which while I did not get the same error when clicking 'Apply now', it complained of not being able to create a file because the directory '~/.config/pulse/ does not exist', even though it does.

---

### Post by ezstyles88 on 2015-10-28
> **whaddyaknow said:**
> I had exactly the same problem since yesterdays upgrade from 15.04 to 15.10. After a LOT of trial and error with hdajackretask, different alsa options etc. to no avail.  In the act of desperation I removed hdajackretask patches, my own patches and added:  options snd-hda-intel model=asus-mode5 (its pin settings map headphones to line out [furthest jack input on the right])  and now my headphones work via line out.  No luck on mic though.

Nice, setting options snd-hda-intel model=asus-mode5 worked to turn my line out  for headphones as well, and will work for now, but I will continue working on getting everything working properly. Thanks for the input. Testing gets tedious after hours and hours :D

I'm curious though, did everything work properly for you in 15.04? And do you have the exact same model laptop?

---

### Post by ezstyles88 on 2015-10-30
Ok so it looks like this is solveable with hdajackretask after all. Simply select both "Show unconnected pins" and "Advanced override" in the Options box Override Pin ID 0x16 Changing Device to: headphones, and Apply now. It is now working for me!

---

