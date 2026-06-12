---
title: "mic doesnt work, hp pavilion dv9730us"
date: 2009-09-25
forum: Hardware
---

### Post by branislavski on 2009-09-25
Hey guys, hope that someone has the magic for this one,
I really  like ubuntu, but mic is a big deal for me cause i do a lot of 
voice/video recording and skype calls.
In the recording tab mic looks muted but makes no difference if i change it.

---

### Post by dagoth_pie on 2009-09-25
In the volume control, bring down the drop down menu and select any of the options with something along the lines of "pulse capture" or "pulseaudio capture" and make sure that the mic volumes in those are turned up. Sound is one of the rough edges at the moment, so it does take some work to get running smoothing a lot of the time.

---

### Post by branislavski on 2009-09-25
Well now i screwed it up, after some major stupidness i have a red x over my volume control and no sound at all after restarting. what do i do now? and by the way after someone helps me gettin it back what drop down box, i see a lot of people posting click edit_prefereces but i never had a top menu like in nautilus. just the pics ive posted.

---

### Post by dagoth_pie on 2009-09-25
Hopefully you've only muted it, double click the volume control and that should unmute it.

I was meaning the drop down box in your pictures, labeled Device: HDA NVidia (ALSA mixer)

Sorry I should have been more specific.

---

### Post by branislavski on 2009-09-25
First of all major thanks for your help dagoth_pie.
I have reinstalled alsa from scratch rebooted, volume is back and volume control accessible, but even after checking all the ones from the drop down menu problem persists. I am worried because it looks like there is alot of people trying to figure out their mic and i really like ubuntu. There has to be a way there always is. ill keep on trying and if you or someone else have some ideas it would be great.

---

### Post by dagoth_pie on 2009-09-25
Usually the first thing I do is go to System/Preferences/Sound and change all four options to Pulse, rather than autodetect, that stops Alsa or Oss from grabing the sound card and not letting applications use it. Then run
```
sudo apt-get install padevchooser
```

Then go to Applications/sound & video/Pulse Audio Device chooser
Up in the top right corner there will now be an icon that looks like a headphone jack, left click it then theres nice set of new options to chose from, the handy one here is "Volume Meter (Recording)". Open it up, and if that moves when you talk into you're mic you'll know that Pulse is picking up the audio fine. Which is a good step towards solving you're problem.

---

### Post by branislavski on 2009-09-25
ive installed the chooser but it doesn't start, it tryies for like ten seconds and never opens.

---

### Post by dagoth_pie on 2009-09-25
Go to therminal and run ```
padevchooser
``` It does the same thing as the menu shorcut but it mean's you can see what error is stopping it from working, just copy and paste what comes up in the terminal here.

---

