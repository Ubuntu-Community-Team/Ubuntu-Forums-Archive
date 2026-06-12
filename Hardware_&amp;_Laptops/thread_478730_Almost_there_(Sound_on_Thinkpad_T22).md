---
title: "Almost there (Sound on Thinkpad T22)"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by aristotlewilde on 2007-06-19
Didn't see anything resembling this when I searched so...

I am running into an issue that may be a simple fix.  I am testing out a Thinkpad T22 to use as my throw around laptop.  I succesfully installed Feisty on it today and have nearly everything working.

However, soemthing is not working with my microphone.  I can hear myself through the speakers or headphones when I talk into it or tap it, but it isn't "capturing".  I mean when I make a Skype Test Call, nothing plays through or when I try to record soemthing in sound recorder, it plays back silent.

This happens in ALSA and OSS.  

Please help.  I am so close to having the perfect setup!   Ok, the perfect setup for a screw around machine...

*Soundcard is a Cirrus Logic

---

### Post by jpeddicord on 2007-06-20
In the Volume Control, go to Edit > Preferences and make sure that everything is checked. Then, play around with the sliders a little until one of them works. If it still does not work, post back here with a screenshot or description of what your volume settings are.

Jacob

---

### Post by aristotlewilde on 2007-06-21
I have done so with the sliders.  I tried both ALSA and OSS.  

I can hear my mic in the headphones clear as day, just nothing captures it.  

I am wonderign if I just don't have capture shut off somewhere else...

---

### Post by msallen on 2007-06-26
Feisty, and supposedly dapper, set up the capture settings for the alsa drivers such that for most people the microphone is not working. You will find a number of threads on this if you search for "ubuntu fiesty microphone problems". None of these solutions were sufficient for me and my trusty T21, although many of them were close. Here is what you must do:

run "alsamixer"
hit "tab" to change to the "capture" menu
highlight "mic" and push space (CAPTUR should appear in red above it)
select "capture" and make sure the volume is turned up
select "adc" and push space (CAPTUR should appear in red above it)

The final step is the critical one for the cs64xx alsa drivers. This alone may not work, but I advise you to peruse the ubuntu forums for a variety of other solutions to fiesty's copious microphone problems covered there. It may be sufficient to run alsamixer again and make sure that none of the options on the basic window are muted (you can toggle mute using "m"... the flag will change from mm to 00 when it is unmuted.

Good luck.

---

### Post by msallen on 2007-06-26
Just an update...

This can all be done using the gnome GUI in a way that is much more user friendly.

- Double click the sound icon on your menu bar. Alternatively, right click on it and select "open volume control"
- Under Edit->Prefrences highlight "Microphone", "Microphone Capture", "Mic Boost", "Mic Select", "Capture", "ADC", "ADC Capture" and close.
- Select the "Recording" tab and make sure this is not muted and is turned all the way up.
- Select the "Switches" tab and toggle "Microphone Capture" and "ADC Capture". You may also select Mic Boost if you feel its necessary (its not for me).

Again, good luck.

---

### Post by fredfelter on 2008-06-24
Just a confirm note that the alsamixer method as outlined above by Msallen worked for me (T22, Ubuntu 8.04) after trying multiple other recommendations from other postings and web sites; in fact I was just about to jettison Linux in frustration when I ran into this thread. Interestingly the gnome-GUI method above, for some reason, didn't do it for me.
A huge thanks to Msallen.

---

