---
title: "Cannot Record Sound or Play MIDI Files"
date: 2009-03-28
forum: Hardware
---

### Post by DevinMcElheran on 2009-03-28
My sound card is working perfectly for sound, but I can't record sound, or play MIDI files. My lspci shows this "00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)" for my sound card. I have no idea why it isn't working. Any help is appreciated.

---

### Post by ajgreeny on 2009-03-28
For midi files you need to install timidity, and timidity-interfaces-extra if you want a GUI for it, and finally freepats for the voices needed.

For recording, what are you using?  I have always found sound-recorder to be unintuitive and not very good so always use audacity, which is an excellent sound editor as well as recorder.  Give that a try and come back again if it is not working.

PS:  I assume your microphone is working OK, and that you have the capture slider in alsa-mixer set high enough.

---

### Post by DevinMcElheran on 2009-03-28
Thanks for the timidity thing, but I have used audacity (and love it), but whenever I try to record (normal sound), it freezes up. Even sound recorder. I have no idea why.

---

### Post by ajgreeny on 2009-03-29
Possibly something to do with pulseaudio, which as far as I'm concerned in Hardy, is nothing more than a nuisance, so I don't use it.  When I did try to use it I had all sorts of problems with applications including audacity.  Make sure your audacity preferences are set correctly for your system, and try all combinations of that in both audacity and sound preferences of the system overall, and you may have some luck.

---

### Post by DevinMcElheran on 2009-03-29
So the problem is pulse audio? And I need to change it to ALSA? Or Jack? I'm a noob, so correct me if I'm wrong. Pulse Audio, Jack and Alsa are different drivers right? So it's all in the settings? Is there anyway to remove Pulse Audio and use a different one? Sorry for bombing you with questions, but I'm new to the "choices" in linux, as opposed to the "no, you have to use this" in microsoft. Thanks.

EDIT: I just looked at my "Sound" settings in preferences, and "sound capture" is set to ALSA. I tested all pf them, most of them gave me this "gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for recording. Device is being used by another application." The only ones that didn't were "test sound" and "silence"

---

### Post by ajgreeny on 2009-03-30
On my system, which I nearly broke as far as sound is concerned by trying to get pulse working, my sound preferences are all set to ALSA and the default mixer is my nVidia sound card (see attached picture)  Try changing your sound preferences in the same way to see if it helps.

---

### Post by DevinMcElheran on 2009-04-01
I tried setting everything to ALSA, but it still doesn't want to go, everything within audacity freezes up when I try to record. All the controls and even the File and Edit buttons bar won't work. I have to force quit it.

---

### Post by DevinMcElheran on 2009-04-09
Can anyone help me with this?

---

