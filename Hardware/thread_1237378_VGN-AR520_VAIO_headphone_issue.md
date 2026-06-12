---
title: "VGN-AR520 VAIO headphone issue"
date: 2009-08-11
forum: Hardware
---

### Post by kenjuku0530 on 2009-08-11
Please forgive this noob for not searching the forums but I am a tad tired of searching for ways to fix this problem.

Basically I am getting no sound from my external speakers through the headphone jack on my laptop, and in all honesty I don't care one bit about my laptop speakers as they simply crappy (audiophile here). So if anyone is willing to help this Linux/Ubuntu noob it would grately be appreciated.

And just for starters everything is unmuted.

If this is in the wrong section feel free to move it where it belongs.

---

### Post by Alfons81 on 2009-08-11
Hi,

there is a bug #209771 reported on launchpad by manuele23:

You have to open a Terminal: Aplications>Terminal

Then you have to write down the follow (  without $ )or copy paste:

$ sudo gedit /etc/modprobe.d/alsa-base

Then it will open a text processor with some code writen inside. You have to add this line at the end ( this time with $ ):

$ options snd-hda-intel model=vaio position_fix=0

then you have the restart your computer and here you have the sound:guitar:.

Hope it works!!!

---

### Post by kenjuku0530 on 2009-08-11
Sorry it didn't work, any other suggestions?

---

### Post by Alfons81 on 2009-08-12
Sorry yesterday when I replied you I was at my work and unfortunetly they don't have Linux on their computers and I couldn't check how I fixed this bug.

When you run this in your terminal ( without $ ), 

$ sudo gedit /etc/modprobe.d/alsa-base

it will open a blank sheet, then you add the follow _without the $_ (yesterday I told yoy with$) :

$ options snd-hda-intel model=vaio position_fix=0

Very important: _Save it_ also yesterday I forgot to tell you to save it ) and _restart your computer_.

I think it must works because I have a a VGN-AR88L and it seems similar as yours. Also people with such different models fix it like that. It could be that you have a different sound card that is not an intel.

If it don't works you could write on the launchpad bug and ask there the link is:

[https://bugs.launchpad.net/ubuntu/+bug/209771](https://bugs.launchpad.net/ubuntu/+bug/209771)

---

