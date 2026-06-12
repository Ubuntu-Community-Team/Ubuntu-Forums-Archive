---
title: "Microphone does not work on Xubuntu 8.10 release and Dell Vostro 1510"
date: 2008-11-09
forum: Hardware
---

### Post by RomanIvanov on 2008-11-09
Hi, ALL,

I installed Xubuntu 8.10 release. All hardware works out of the box except for build in microphone.

I used "Volume Control" to set "Capture" and "Front Mic Boost" and "Digital" sliders to the max value.
Checked values in "sudo alsamixer" - all values are on max.

Check it in "gnome-volume-control" - "Capture" is muted. I tried switch on and rerun "gnome-volume-control" - recording sliders are MUTED again - no way to save max level here.

I try to record sound from microphone in "Sound Recorder" and "Audacity" - no luck :(. Problem with recording. Skype does not work either.

My mic is not dead I checked it in Vista. Please help I am in despair, I have read a ton of forums and blogs, .... .

Thanks in advance.

---

### Post by RomanIvanov on 2008-11-09
lspci:

00:1b.0 Audio device: Intel Corporation 82801H (ICH Family) HD Audio Controller (rev 03)

---

### Post by RomanIvanov on 2008-11-18
Finally I get microphone to work but partly - only by remote mic that is connected to my laptop font panel by "male connector".

Here is resources for whom who steel in need:
[http://www.linux-on-laptops.com](http://www.linux-on-laptops.com) - find similar model to see how problem was solved, even page for similar model could help.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) - great article.

---

### Post by RomanIvanov on 2008-11-18
And now some tricks of making at least  external mic work:

1. Install 8.10 Xubuntu
2. Install all updates by UpdateManager
3. run "gnome-sound-recorder"('Sound Recorder'). Beware have a lot of bugs - that mislead you from correct way.
4. Run "gnome-volume-control"('Volume Control') from 'Sound Recorder' through menu "File/Open Volume Control" and keep it open.
5. Make 'Volume control' to show you all sliders that you have (Press ‘Preference’ and select all items in list). Device = ‘HDA Intel (alsa mixer)’.
6. Unmute all sliders in tab 'Recording' and ‘Playback’
7. On tab 'Options' put first Input source in "Front Mic" and second, if there is such option to "Mic".


Now you need to play with 'Sound Recorder' and 'Recording' tab of 'Volume control'.
1. set up in 'Sound Recorder' as ‘Record input source’ 'Front Mic Boost', and ‘Record as’ = ‘Voice, lossless (.wav type)’.
2. raise 'Capture', 'Capture1', 'Digital' to 100% and 'Front Mic Boost' on tab ' Playback' to 100%.
3. Switch to 'Sound Recorder' and try to record.
4. If you failed hear yourself - do not give up! Lower sliders and try again.
5. Beware that 'Sound Recorder' sometimes change settings of 'Recording' tab sliders without asking you!!!!! Keep 'Volume Contol' always in front of you - to control the process, and unmute again and again till you win microphone.

My settings:
Master - 100
Headset - 84
PCM - 100
Front - 81
Front Mic Boost - 100
Capture - 61
Capture1 - 3
Beep - 0
Digital - 33
Input So - Front Mi
Input So – Mic

Attention to my winning formula:
Capture - 61
Capture1 - 3
Digital - 33

Example that does not work for me but highly advisable in other threads !!!!:
Capture - 100
Capture1 - 100
Beep - 0
Digital - 100
In this case no sound recorded. So you need to play with sliders!! Do not give up!!

---

### Post by RomanIvanov on 2008-11-18
If you know how to make my internal mic work - please let me know.

---

