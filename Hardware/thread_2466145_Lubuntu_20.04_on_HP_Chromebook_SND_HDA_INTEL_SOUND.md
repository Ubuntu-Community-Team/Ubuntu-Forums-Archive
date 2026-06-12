---
title: "Lubuntu 20.04 on HP Chromebook SND_HDA_INTEL SOUND: NO SOUND DUMMY OUTPUT"
date: 2021-08-20
forum: Hardware
---

### Post by zer03755 on 2021-08-20
I have found this to be a common problem floating around forums and the web. I have tried a lot of the solutions provided and have had no luck. 

Everything works perfectly fine with my set up. But there's no sound. And the output device is stuck on dummy output. 

I'm relatively experienced with Linux but definitely have a lot to learn. Is there anyone that can help me with this? I have just completely reloaded the computer again to start with a clean slate in trying to resolve the issue.

---

### Post by guiverc on 2021-08-20
Have you looked at any of the documentation?

- [https://help.ubuntu.com/community/TroubleShootingGuide](https://help.ubuntu.com/community/TroubleShootingGuide)

yes you're using Lubuntu and could look at their docs too, but they relate mostly to the Lubuntu/LXQt unique parts of the system, where sound is part of the Ubuntu base; thus Ubuntu documentation applies more here.  At the bottom of that wiki you'll find the Sound troubleshooting page

- [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

It will provide ways to explore your system and gain details of your chipset. 

 Myself I usually just `sudo lshw -C sound`  (ie. list-hardware of class sound) and you'll get clues as to status if something is recognized (by the linux kernel) or it has issues that need fixing. If nothing is recognized, the more detailed info in the *SoundTroubleshootingProcedure* will help more.

---

### Post by bobunderwood99 on 2021-08-20
I haven't tried this but it seems on point [https://gist.github.com/jeremy-breidenbach/92fc648ed2590ff9cd3a0ae57ed98e4a](https://gist.github.com/jeremy-breidenbach/92fc648ed2590ff9cd3a0ae57ed98e4a)

---

### Post by zer03755 on 2021-08-21
Thank you for your respomse. I ran through the troubleshooting and the only one that I was unable to get to work was number 5

> [h=3]5. Do you have the sound modules installed?[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Open a terminal and type[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]find /lib/modules/`uname -r` | grep snd[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]You should see a large list of items come up. If you don't, it means that the install process did not install the sound modules for you. To fix this, type in the terminal window:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo apt-get install linux-restricted-modules-`uname -r` linux-generic[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]After installing the modules, you will need to reboot for the changes to take effect.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]If the modules are already installed, proceed to the next step to check to see whether your hardware is recognizing the sound card as installed.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]




The results of the commands was that it was unable to find the directory and the packages to install. All the other troubleshooting resulted in positive results but my sound still doesn't work =*(

---

### Post by zer03755 on 2021-08-21
None of this seems to have worked either. It updated some stuff. But still no sound. Still nothing but dummy output.

---

### Post by tea for one on 2021-08-21
Have you seen the info here [https://wiki.galliumos.org/Hardware_Compatibility](https://wiki.galliumos.org/Hardware_Compatibility)

Just offering alternative suggestion - no direct experience

---

### Post by bobunderwood99 on 2021-08-21
What method did you use to install Ubuntu? Linux on Chromebook (Crostini) or Crouton or Mr. Chromebox or ? And what version of Chrome OS are you running (if not Mr.Chrmbx)?

---

### Post by zer03755 on 2021-08-24
I used Mr. Chromebox. So there's no ChromeOS on the computer at all not. Which was my goal and I really love. The only issue I have is this sound issue.

---

### Post by zer03755 on 2021-08-24
So I have the KIP

[TABLE="class: wikitable sortable jquery-tablesorter"]
[TR]
[TD]HP Chromebook 11 G3/G4/G4 EE[/TD]
[TD]KIP[/TD]
[TD]2015[/TD]
[TD]Intel Bay Trail[SUP][[9]]("https://wiki.galliumos.org/Hardware_Compatibility#cite_note-BayTrail-9")[/SUP][/TD]
[TD="bgcolor: #CCFFCC, align: center"]Yes[/TD]
[TD="bgcolor: #CCFFCC, align: center"]Required[SUP][[2]]("https://wiki.galliumos.org/Hardware_Compatibility#cite_note-Firmware-2")
[/SUP][/TD]
[/TR]
[/TABLE]

It says it works but it needs a firmware update. I ran through the firmware update process and it hasn't changed anything 

=(

---

### Post by bobunderwood99 on 2021-08-25
> **zer03755 said:**
> So I have the KIP

[TABLE="class: wikitable sortable jquery-tablesorter"]
[TR]
[TD]HP Chromebook 11 G3/G4/G4 EE[/TD]
[TD]KIP[/TD]
[TD]2015[/TD]
[TD]Intel Bay Trail[SUP][[9]]("https://wiki.galliumos.org/Hardware_Compatibility#cite_note-BayTrail-9")[/SUP][/TD]
[TD="bgcolor: #CCFFCC, align: center"]Yes[/TD]
[TD="bgcolor: #CCFFCC, align: center"]Required[SUP][[2]]("https://wiki.galliumos.org/Hardware_Compatibility#cite_note-Firmware-2")
[/SUP][/TD]
[/TR]
[/TABLE]

It says it works but it needs a firmware update. I ran through the firmware update process and it hasn't changed anything 

=(

What is "it" and what did you do to update the firmware? 

Which BIOS did you originally install - Legacy or UFEI?

Please run

```
sudo inxi -Ab
```

in a terminal and post the output wrapped in code tags.

---

### Post by NoWayWin8 on 2021-11-04
> **zer03755 said:**
> I have found this to be a common problem floating around forums and the web. I have tried a lot of the solutions provided and have had no luck.

I had the same problem and after much digging the issue seems to be Intel's BayTrail sound card "chtmax98090" which is not supported in the version of ALSA included with Ubuntu. I ended up installing Manjaro Linux and the sound works perfectly.

Manjaro uses ALSA 1.2.5.1 while Ubuntu uses 1.2.2. According to the documentation on alsa-project.org, support for chtmax98090 was added in ALSA version 1.2.3. Unfortunately neither Ubuntu/Lubuntu 20.04.3 nor 21.10 have this updated ALSA.

---

