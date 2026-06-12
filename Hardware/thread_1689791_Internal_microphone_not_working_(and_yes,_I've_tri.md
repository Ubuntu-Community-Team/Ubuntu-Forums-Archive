---
title: "Internal microphone not working (and yes, I've tried that!)"
date: 2011-02-17
forum: Hardware
---

### Post by MartinTheWarrior on 2011-02-17
Alright, so although I'm new to Ubuntu - one of the first things I discovered upon installing 10.10 Maverick on my Acer Aspire AOA150 was that the microphone doesn't work. (Yes, I've tried it in multiple programs).

So this led to Google-fu, and three days (probably about six hours total) of trying everything possible to get it to work...so if you can fix this, you are a genius and I am forever in your debt.

So here are a few things I've tried along the way, just so we know what is NOT working and such.

> 
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

[http://www.alsa-project.org/db/?f=a99f5cfa9e25c22a34bafa0a32a3def6e4c8ed1a](http://www.alsa-project.org/db/?f=a99f5cfa9e25c22a34bafa0a32a3def6e4c8ed1a)




Now I've gotten the linux-backports-modules-alsa-maverick-generic installed, and I've ensured I'm using the upgraded alsa - I also have alsamixer (nothing is muted or turned off - sound card allows me to choose between default and my HDA - neither seems to bring the microphone to life)

I have PulseAudio, I have ensured it is updated and everything.

I have tried setting an input bar for left speaker to 100% and right speaker to 0% (and vice versa, and tried in between)

I have tried opening alsa-base.conf and adding[FONT=monospace] 'alias snd-card-0 snd-hda-inteloptions snd-hda-intel model=acer' (and acer-aspire)

I have tried inserting "amixer set 'Capture' cap" in rc.local

This last one seemed the most promising, but the instructions ended with [/FONT][I]Then I double clicked on my volume icon to bring up the sound mixer and 
went to edit --> prefs --> and checked "input source"
it then made an "options" tab on my mixer panel and I selected "Front Mic"[/I] -- and when **I** click on the volume icon it doesn't do anything, a single-click brings up the options for the sliderbar, "RhythmBox" and "Sound Preferences", and nowhere in "Sound Preferences" can I bring up edit/prefs/inputSource and assuming "my mixer panel" is the same as alsamixergui or alsamixer on the terminal, I cannot bring up any options that have the word "Front Mic" anywhere. (terminal alsamixer does allow me to F4 and I can change input device from "default" to "HDA" but neither seems to do much)

So, any thoughts?

---

### Post by marin123 on 2011-02-17
i'm a bit confused what you were doing in sound preferences, so im going to ask this: did you change Connector in Input tab?
try all of the options for all of the cards and see if Input level moves when you speak.

---

### Post by MartinTheWarrior on 2011-02-17
I did change it, I've tried just about every combination of Line-In, Microphone 1 and Microphone 2 - now if I use Microphone 1 with a headset, then I plug in and both Skype and Sound Recorder will recognise my voice - so it works. But internal Mic doesn't work whether I'm on Microphone 2, 1 or Line-In (which one SHOULD I be on, theoretically, for internal mic? and do I need to make sure Sound Preferences and AlsaMixer are both configured to the "same" one? Asalamixer gives me the option of Line, Mic, Internal Mic - Sound preferences gives me the choice of Line-In, Microphone 1 and Microphone 2 (and since Mic 1 works with headset, I'm assuming that make Mic2 the same as Internal Mic)

---

### Post by marin123 on 2011-02-18
Microphone 2 is internal mic on my laptop (acer 5942G) and it works all the time.

i'm sending my screenshot of alsamixer, i hope it helps :)

---

