---
title: "Sound Fixed: Toshiba A135-S4467 HDA INTEL Realtek ALC861-VD"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by dsbeav on 2007-07-15
This is what I did to finally get my Toshiba A135-S4467 with soundcard and driver HDA INTEL Realtek ALC861-VD  to work properly.  That includes turning off my PC Speakers when I put in headphones.

First you need to get the realtek6 Alsa Driver patch from: 

[https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=1955&type=bug](https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=1955&type=bug)

Next go to

[http://www.alsa-project.org/](http://www.alsa-project.org/)

Download the newest versions of:

Drivers
Libraries
Utils
OSS

At this time the newest version is 1.0.14.  (This is the version I used)

Follow the instructions at this link for patching, compiling and configuring the downloaded files.

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG).

Last step. 

Edit /etc/modprobe.d/alsa-base

Add the following line:

options snd-hda-intel position_fix=1 model=lenovo

(If this line already exists with a different model, change the model to lenovo)
This line mutes your pc speakers when you plug in headphones.

This is what worked for me.  Hopefully it will work for other people!


Take care

---

### Post by Cappy on 2007-07-23
Thanks this worked perfectly for me! I used patch Realtek18 and the alsa rc4  =)
I thought it wasn't working when I first booted up but I just had to raise the PCM on my playback and then hit the headphone switch on the "Switches" tab to make it work perfectly. 

Here is the correct link for the patches:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2725](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2725)

Running a new A135-S4666 laptop.

---

### Post by stchman on 2007-07-23
> **dsbeav said:**
> This is what I did to finally get my Toshiba A135-S4467 with soundcard and driver HDA INTEL Realtek ALC861-VD  to work properly.  That includes turning off my PC Speakers when I put in headphones.

First you need to get the realtek6 Alsa Driver patch from: 

[https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=1955&type=bug](https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=1955&type=bug)

Next go to

[http://www.alsa-project.org/](http://www.alsa-project.org/)

Download the newest versions of:

Drivers
Libraries
Utils
OSS

At this time the newest version is 1.0.14.  (This is the version I used)

Follow the instructions at this link for patching, compiling and configuring the downloaded files.

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG).

Last step. 

Edit /etc/modprobe.d/alsa-base

Add the following line:

options snd-hda-intel position_fix=1 model=lenovo

(If this line already exists with a different model, change the model to lenovo)
This line mutes your pc speakers when you plug in headphones.

This is what worked for me.  Hopefully it will work for other people!


Take care

I have a Toshiba laptop (A135-S2246) with the SB450 sound card.  Did you ever come across a fix for that card too.  I have sound on my laptop, but when I put headphones in the external speakers keep playing.

Thanks

---

### Post by Cappy on 2007-07-24
ARGH so I finally upgraded my laptop today (kernel from .15 to newest .16). Soon as I did sound stopped working. I tried ```
sudo make install
``` since I still had my folders but no go. I had to ```
sudo make clean
``` on each folder and recompile each one. Working now with OSS only. ALSA stopped working! I've recompiled it a few times, but ALSA just will not work anymore on either kernel! It was working fine on .15 until I upgraded =( Now it just says "Cannot open resource for writing" when I try to use an application that uses ALSA.

Edit:
Fixed it, had to ```
rm ~/.asound*
```
and it works perfectly again (with ALSA!). I'm glad I remembered reading that on a guide on how to upgrade from edgy to feisty .. I was running out of ideas.

---

### Post by Bittersweet Chaos on 2007-08-19
I was following your instructions, copy and pasting and this happened.......

em@em-laptop:~/alsa-src$ tar xvf realtek6.tar.gz
tar: realtek6.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


I'm very very new to Ubuntu and Linux in general and as a result have no idea what this means or what I'm supposed to do now.

Please help.

-Em

---

### Post by luter on 2007-08-31
works great on toshiba satellite a135-s4527 :) thanx

---

### Post by angelinux on 2007-08-31
It worked fine on a Fujitsu-Siemens AMILO PRO V3505, except for the microphone, that stills not working properly (too poor level).

I Also cannot use any softphone.

I followed the instructions, applyng the realtek19 patch (the last I can find).

Hope it can be useful to others

---

### Post by Dave Crowhurst on 2007-09-01
Can someone please do a very simple to follow set of instructions for this fix please. I would really like to get some sound out of my new Acer Aspire 5710.

Thanks.

---

### Post by cpurodriguez on 2007-09-06
I'm in the same situation with the same ACER model. 

I've tried what's posted on the "HdaIntelSoundHowto" thread unsuccessfully. 

Thanks in advanced

---

### Post by CalvinK on 2007-09-28
> **cpurodriguez said:**
> I'm in the same situation with the same ACER model. 

I've tried what's posted on the "HdaIntelSoundHowto" thread unsuccessfully. 

Thanks in advanced

Just go to [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) and download the files of alsa
alsa-src/alsa-driver-1.0.15rc2.tar.bz2, alsa-utils-1.0.15rc1.tar.bz2, alsa-lib-1.0.15rc2.tar.bz2. Put them in a directory called, by exemple, alsa-src. tar or gunzip the files, then go to the newly created directories and type : "/etc/init.d/alsa-utils stop " . then "/configure" then "make" (without quotes), then "sudo make install" following the directives of alsaproject Matrix:Module-hda-intel @ [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)
From AlsaProject (searching for your card driver. Your new alsa is ready. The realtek patch is included in the new version. 
"Sudo gedit /etc/modprobe.d/alsa-base" and add at the end 
options snd-hda-intel position_fix=1 model=lenovo. 
That's all folks !! Go to the gnome-sound-controller (in a console if you want) . Shut all the mics in the playback part, then go to Capture and choose the mic. Reboot and enjoy (or I hope so). You can also use alsamixer. To access the capture type Tab.:)

---

### Post by peabody on 2007-09-28
**A little ignorance is dangerous, I don't have the same soundcard, I have an HDA intel Conexant 5045 (CX2059).  Disregard post.**

I have the same soundcard on my compaq presario C571NR.  I didn't have to use any patch, I just downloaded the alsa-driver, alsa-lib, and alsa-utils packages version 1.0.14 and compiled and installed each of those.  Then I added the following to the end of the /etc/modprobe.d/alsa-base file:

snd-hda-intel model=laptop

That worked for me (fixed the speakers not muting when headphones plugged in at least).  I had to repeat the process upon kernel upgrade.  Microphone only works in Audacity via the OSS interface, although it seems to work perfectly in Skype 1.4.0.99 which I thought used ALSA.  Latest Jokosher seems to be having serious problems recording via gstreamer (using feisty packages from the jokosher website).  I also have been completely unsuccessful in trying to get sound using the OSS driver in the included wine (v. 0.9.33).  I'd like to get this working as I'd like to have sound with my Half Life.

EDIT: I see the post above is advocating using the 1.0.15rc2 packages.  While those might have worked for him, they gave me issues.  The speakers would "pop" ever time the soundcard started to be used.  They did work, but I had much better behavior out of the 1.0.14 drivers.

---

