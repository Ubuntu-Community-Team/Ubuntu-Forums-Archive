---
title: "No sound through speakers Toshiba NB200"
date: 2010-04-16
forum: Hardware
---

### Post by web1star on 2010-04-16
Hi I managed to solve this issue:
CODE:
sudo gedit /etc/modprobe.d/alsa-base.conf

then add at the end of the file: 

options snd-hda-intel model=auto

reboot
And your Toshiba NB200 or NB205 /USA/ has perfect sound from your  internal speakers:
Enjoy

---

### Post by cemzafer on 2010-05-02
I have the same problem, but there is no any line in the alsa-base.conf in Ubuntu 10.04.

options snd-hda-intel ...

Thanks.

---

### Post by wford002 on 2010-05-02
I can confirm that this works, I have an nb200, thanks for posting.

@cemzafer just copy and paste that line (options snd-hda-intel model=auto) at the end of the file, save, and reboot.

---

### Post by kelvingeorge on 2010-05-05
> **web1star said:**
> Hi I managed to solve this issue:
CODE:
sudo gedit /etc/modprobe.d/alsa-base.conf

then add at the end of the file: 

options snd-hda-intel model=auto

reboot
And your Toshiba NB200 or NB205 /USA/ has perfect sound from your  internal speakers:
Enjoy

Thank you.This worked for me on NB205.

---

### Post by Fourcultures on 2010-05-06
> **web1star said:**
> Hi I managed to solve this issue:
CODE:
sudo gedit /etc/modprobe.d/alsa-base.conf

then add at the end of the file: 

options snd-hda-intel model=auto

reboot
And your Toshiba NB200 or NB205 /USA/ has perfect sound from your  internal speakers:
Enjoy

Just to confirm: this worked for me too, perfectly. I'm running 10.04 NBR on a Toshiba NB200. Thanks! 

I'd just add that for anyone still stuck with no sound on an NB200, you're not missing much. The tinny-sounding speaker is the only bad thing on this netbook.

Fourcultures

---

### Post by GuiGuy on 2010-05-15
> **web1star said:**
> Hi I managed to solve this issue:
CODE:

options snd-hda-intel model=auto


Nice one. Works great on my NB200. Many thanks

---

### Post by lidex on 2010-05-16
web1star, can you mark the thread as solved please?

---

### Post by filias on 2010-06-09
Hi,

this doesn't solve the problem in my case.
Does this solution have any dependencies?
Is there any alternative solution?

Thanks in advance

---

### Post by lidex on 2010-06-09
> **filias said:**
> Hi,

this doesn't solve the problem in my case.
Does this solution have any dependencies?
Is there any alternative solution?

Thanks in advance

Do you have NB200?
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by fodz on 2010-06-10
Yep! This worked great!! Added the line of code and worked like a charm!

---

### Post by Jammerton on 2010-06-21
WOW!!! It actually worked!!! I had almost given up.  this must be the tenth or eleventh fix I've tried and unlike the others it actually worked!  Hats off to you, now I can enjoy the crappy nb205 speaker I never needed in the first place.

---

### Post by dabl on 2010-06-21
The best fix for crappy sound on the NB200/205 is a good set of headphones.   :lolflag:

---

### Post by OldSmoky2 on 2010-08-18
Awesome! I've been looking for a couple weeks for a laptop for a friend who ended up in a nursing home/rehab center (with free wi-fi available). Yesterday I got a Toshiba 205 from someone who killed it with a Windows virus and was told it would take $200 to repair. He just bought a new netbook instead. So I installed 10.04 netbook remix on it last night and it worked great except for no sound and painfully slow boot time. Adding the line of code at the end of the alsa file worked perfectly for the sound (such as it is on these) and another forum post supplied an easy fix for the boot time.
Thank you.:D

---

### Post by StevenTurner on 2010-09-26
Works as described on NB200  running Netbook 10.04 remix, thanks :)

---

### Post by ManicStudio on 2011-02-11
This worked for me too!
Ubuntu 10.04, Toshiba NB200.
Thanks, great job!
:D

---

### Post by hp4805 on 2012-09-20
> **web1star said:**
> Hi I managed to solve this issue:
CODE:
sudo gedit /etc/modprobe.d/alsa-base.conf
 
then add at the end of the file: 
 
options snd-hda-intel model=auto
 
reboot
And your Toshiba NB200 or NB205 /USA/ has perfect sound from your internal speakers:
Enjoy
 
Hi...i am having this no sound problem with my NB200 Toshiba running on W7, I tried above at command prompt. 
sudo gedit /etc/modprobe.d/alsa-base.conf
it says sudo is not recognized
 
Appreciate help
Thanks

---

### Post by hp4805 on 2012-09-20
> **Jammerton said:**
> WOW!!! It actually worked!!! I had almost given up. this must be the tenth or eleventh fix I've tried and unlike the others it actually worked! Hats off to you, now I can enjoy the crappy nb205 speaker I never needed in the first place.
 
can you go through with me step by step process to get sound on this nb200
i am running on windows 7 OS

---

### Post by hp4805 on 2012-09-20
please , can you let me know step by step process to get thos nb200 sound working 
thanks

---

