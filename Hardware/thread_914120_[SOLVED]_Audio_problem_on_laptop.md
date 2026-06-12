---
title: "[SOLVED] Audio problem on laptop"
date: 2008-09-08
forum: Hardware
---

### Post by Jayjem on 2008-09-08
Hi guys!

Everything is working perfect out of the box with Ubuntu apart from one small problem... the audio.

It's working partially but the earphone jack doesn't seem to block out sound coming from the built in laptop speakers. This isn't a physical problem because it works perfectly fine in Windows.

Here is some information of my sound device from the system information utility in Windows:

```

Name: Realtek High Definition Audio

Manafacturer: Realtek

Status: OK

PNP Device ID: HDAUDIO\FUNC_01&VEN_10EC&DEV_0262&SUBSYS_1041D1600&REV_1001

Driver: C:\windows\system32\drivers\rtkhdaud.sys (5.10)

```

It says it's using the Intel HDA drivers inside Ubuntu on the Sound properties dialog.

Now, if I remember rightly my sound worked perfectly with an earlier version of Ubuntu (7.10 and below I'm sure). Why doesn't it work with 8.04?

I'd like to get this fixed because this is what is stopping me from letting Ubuntu be my main operating system.

**EDIT:** My laptop model is a Sony Vaio VGN-N11H.

Much help appreciated,
John

---

### Post by Jayjem on 2008-09-08
After finding out my sound card model I got a fix:

> 
Have a fix!



What I've done:



Code:



sudo apt-get install m-a

sudo m-a prepare

sudo m-a a-i alsa



Then, in a terminal gksudo gedit /etc/modprobe.d/alsa-base and, at the end, add the following: options snd-hda-intel model=sony-assamd



Now I get the sound right: I get sound from the speakers and these mute when I plug-in the headphones. As for the microphone, it sort of works, but it's very noisy, not usable.



Hope it helps!



EDIT: the headphones stuff also works by using model=benq-t31



EDIT2: after some more testing, I've found that the models that work are hippo, benq-t31 and sony-assamd.


Can't remember who wrote this post (as I saved it to a text file to quickly check if it worked) but thank you... thank you very much. :)

Perhaps Ubuntu can be my main OS now, we'll see... :p

---

### Post by ecsdrive on 2008-09-08
It is probably something related to ALSA because I also had some problems with the audio on the Intel HDA (microphone didn't work at all, very low sound volume) and an update to Intrepid solved all sound related problems
You also should try to enable all the options from the sound module (Preferences) because some cryptic option might just fix the microphone problem, or actually enable it

---

