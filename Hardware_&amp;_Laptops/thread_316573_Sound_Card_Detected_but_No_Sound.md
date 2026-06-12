---
title: "Sound Card Detected but No Sound"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by Avian00 on 2006-12-11
Hello,

I just received my new laptop, a Toshiba Satellite P105-S9722.  It is working fantastically, except for one show-stopping problem... I get no sound from the speakers or headphone jack.  The sound card is an Intel 82801G (ICH7 Family) High Definition Audio Controller.  It seems to be recognized by the system on all levels.  Gnome Volume Control is happy and all the audio files I play seem to go just fine.  I simply get no sound.  Having searched this forum and googled extensively, I've discovered that my particular series of sound card (the Intel ICH7 Family) is notorious for having this problem.  I've tried re-compiling Alsa using a howto (which I can no longer find) on the Ubuntu Docs site, and I have tried inserting almost every model available for this family in the "/etc/modprobe.d/alsa-base" file.  Still nothing.  Does anybody out there know what I might be missing here?  Better yet, is there anybody with this model of laptop that has gotten the sound to work?  ANY advice would be VERY much appreciated here, even if it's to point me to a better thread on this particular subject.

Thanks in advance!

---

### Post by renzokuken on 2006-12-11
I have this exact problem with another Audio chip (nForce RCP51).

First port of call would be to check alsamixer and make sure nothing is muted. didnt work for me but it might for you.

just type

```
alsamixer
```

at the command line (tab key moves between tabs) "m" unmutes things

---

### Post by Avian00 on 2006-12-11
> **renzokuken said:**
> I have this exact problem with another Audio chip (nForce RCP51).

First port of call would be to check alsamixer and make sure nothing is muted. didnt work for me but it might for you.

just type

```
alsamixer
```

at the command line (tab key moves between tabs) "m" unmutes things

Sorry.  No go.  Absolutely nothing is muted.  But thanks for the suggestion.

---

### Post by Bronco200 on 2006-12-12
HeyHo,

i had the same problem after Edgy installation, although the live CD works perfectly.
I've get my sound back after switching the device from auto to the explicitly device in the GNOME audio settings.

Bronco

---

### Post by Avian00 on 2006-12-12
> **Bronco200 said:**
> HeyHo,

i had the same problem after Edgy installation, although the live CD works perfectly.
I've get my sound back after switching the device from auto to the explicitly device in the GNOME audio settings.

Bronco

Thanks.  Unfortunately, that didn't work for me either.

---

### Post by Avian00 on 2006-12-12
Well I just came across another thread ([http://ubuntuforums.org/showthread.php?t=251877](http://ubuntuforums.org/showthread.php?t=251877)) and after reading it, I got my sound to work.

It seems that if you are the owner of a Toshiba P105 laptop, you must disable ACPI by adding ACPI=OFF to your Grub menu.lst file.  Disabling ACPI causes the sound to magically start working, however at the expense of all "laptop" features (such as power-saving and battery monitoring).  *sigh*  Not really a solution, but it's a step in the right direction.  Does anybody have any suggestions on how to have sound *and* ACPI at the same time?

---

### Post by HellSpawn on 2007-06-06
Some people has fixed this issue by debuging their DSDT Table and recompiling the Kernel, that did't work for me though... :(:confused:

---

