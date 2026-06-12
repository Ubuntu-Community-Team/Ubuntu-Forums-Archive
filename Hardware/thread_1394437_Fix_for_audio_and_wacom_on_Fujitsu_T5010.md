---
title: "Fix for audio and wacom on Fujitsu T5010"
date: 2010-01-30
forum: Hardware
---

### Post by chitarrino on 2010-01-30
I just bought a Fujitsu Lifebook T5010 (FPCM11323), but I encountered some difficulties getting some components to work on a fresh installation of 9.10 Karmic.
I am posting these informations for all those who are having a hard time configuring audio input and wacom digitizer.

Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03).
Microphone was not working. Alsamixer was displaying wrong devices. I simply had to edit this file:
```
gksu gedit /etc/modprobe.d/alsa-base.conf 
```
and add this line at the bottom:
```
options snd-hda-intel model=fujitsu
```
After reboot audio I/O is 100% working.

-Stylus could not be calibrated, stylus buttons didn't work, and input tablet rotation did not follow screen rotation.
My solution was to edit this file:
```
gksu gedit /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
```
and replace its contents with the configuration file named Favux_new-generic_rc2_10-linuxwacom.fdi that I found here: [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949) (registration needed).
After rebooting, I could calibrate the stylus by running:
```
wacomcpl
```

For screen rotation (or screen orientation), I found a simple script here:
[http://blog.aliencam.net/articles/ubuntu-9-04-setup-guide/](http://blog.aliencam.net/articles/ubuntu-9-04-setup-guide/)

Tablet buttons can't be used yet, as the driver fjbtndrv does not compile under Karmic.
I hope these info can be helpful.

---

### Post by Favux on 2010-01-30
Hi chitarrino,

For the fjbtndrv try the ppa linked by omskates in [post #709]("http://ubuntuforums.org/showpost.php?p=8478326&postcount=709").

Is yours one of those that includes multi-touch?  If so could you tell me which bios version you have?  Did you update it or any other firmware?

---

### Post by chitarrino on 2010-02-01
BIOS:
```
Vendor: FUJITSU // Phoenix Technologies Ltd.
	Version: Version 3.05 
	Release Date: 08/20/2009
```

It came with my Lifebook.

That PPA you pointed me won't install.  If I try to install the PPA's manually, only the first dependency does, the one for the kernel. Not the main one.

---

### Post by megpilk1 on 2011-01-13
> **chitarrino said:**
> I just bought a Fujitsu Lifebook T5010 (FPCM11323), but I encountered some difficulties getting some components to work on a fresh installation of 9.10 Karmic.I am posting these informations for all those who are having a hard time configuring audio input and wacom digitizer.Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03).Microphone was not working. Alsamixer was displaying wrong devices. I simply had to edit this file:[code]and add this line at the bottom:[code]After reboot [[COLOR=#000000]audio[/COLOR]](http://www.changeformat.net/change-divx-dvd-format/change-divx-dvd-to-cowon-a2.html) I/O is 100% working.-Stylus could not be calibrated, stylus buttons didn't work, and input tablet rotation did not follow screen rotation.My solution was to edit this file:[code]and replace its contents with the configuration file named Favux_new-generic_rc2_10-linuxwacom.fdi that I found here: [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949) (registration needed).After rebooting, I could calibrate the stylus by running:[code]For screen rotation (or screen orientation), I found a simple script here:[http://blog.aliencam.net/articles/ub...4-setup-guide/](http://blog.aliencam.net/articles/ubuntu-9-04-setup-guide/)Tablet buttons can't be used yet, as the driver fjbtndrv does not compile under Karmic.I hope these info can be helpful.Nice writing, Thanks for your sharing!

---

### Post by rasperin on 2011-10-26
> **chitarrino said:**
> For screen rotation (or screen orientation), I found a simple script here:
[http://blog.aliencam.net/articles/ubuntu-9-04-setup-guide/](http://blog.aliencam.net/articles/ubuntu-9-04-setup-guide/)

Tablet buttons can't be used yet, as the driver fjbtndrv does not compile under Karmic.
I hope these info can be helpful.

Sorry for gravedigging this but that link no longer exists and I'm trying to get auto-rotate to work :(. Google is also failing me :(. Anyone by chance have a write up on how to configure my screen to rotate in kde when I flip it around? (For those who don't have T5010's you can rotate the screen 180degrees and close the lid so all that is showing is the screen instead of the back cover).

Seriously, any help would be hugely appreciated.

Thanks!

---

### Post by Favux on 2011-10-26
Hi rasperin,

Most folks were using the fjbtndrv from this PPA: [https://launchpad.net/~khnz/+archive/ppa](https://launchpad.net/~khnz/+archive/ppa)  because in addition to rotation it gave you the bezel buttons.  But he hasn't updated it for Natty or Oneiric.  So if you're on either of those releases you'll have to see if someone else is updating fjbtndrv.

Of course you could decompose it and pull out the rotation script and try to update it yourself.  Or you could use say a method 1 script on the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

---

