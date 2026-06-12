---
title: "Sound will work after reboot but then stops working for all apps playing sound"
date: 2008-11-08
forum: Hardware
---

### Post by jf1991999 on 2008-11-08
I upgraded to 8.10 immediately it was released and had a number of problems.  Most have now settled down apart from this strange issue.

Immediately after a reboot, I am able to play music via Rhymbox and listen to internet radio through firefox and mplayer.  However after what can be a short time after reboot, if I haven't launch an audio app immediately Rythmbox and Firefox will not play back audio.  Rythmbox fails by not starting to play and the firefox plugins appear to buffer the audio but never play any sound.

I have noticed that sometimes closing firefox will fix the issue, however this works only in about 30% of cases.  Often skype will be the one app that will still work when all others fail.  Sometimes making a skype call will enable the other sound apps to start to work again.

I have tried to track down what causes the audio to stop working.  I had thought that Firefox was causing the problem, but can't repeat this.

I am using an HP Pavilion dv6000.  When the sound works it works very well.  Any help to resolve this would be appreciated.

---

### Post by Airfoot on 2008-11-08
I had a similar problem that was fixed by disabling pulse audio. In terminal :    $ pulseaudio -k
then make sure you are using ALSA for your sound devices (system > preferences > sound)
then in terminal :    $ sudo alsa force-reload
then right click your volume control and make sure to raise the volume.
if this fixes the problem then go to (system > preferences > session) and deselect pulse audio for start-up.

---

### Post by jf1991999 on 2008-11-09
> **Airfoot said:**
> I had a similar problem that was fixed by disabling pulse audio. In terminal :    $ pulseaudio -k
then make sure you are using ALSA for your sound devices (system > preferences > sound)
then in terminal :    $ sudo alsa force-reload
then right click your volume control and make sure to raise the volume.
if this fixes the problem then go to (system > preferences > session) and deselect pulse audio for start-up.

Actually,  I just found that if I quit skype the sound starts to work again.  So it appears that it is skype that is somehow blocking the audio.  I have found that if you make a call with skype the audio will start working again for other apps.  You can quit and then restart skype and have the sound work for a while.  I am not sure what causes skype to block the audio.  I did try your suggestion above and it didn't help the situation.

---

### Post by Airfoot on 2008-11-09
If Skype is the problem then your sound conferencing might be conflicting with your media sound playback try going into "system > preferences > sound" and change the conferencing system to something other than the system you have for media playback and sound events.

---

### Post by jf1991999 on 2008-11-09
> **Airfoot said:**
> If Skype is the problem then your sound conferencing might be conflicting with your media sound playback try going into "system > preferences > sound" and change the conferencing system to something other than the system you have for media playback and sound events.

I changed the Sound settings 'Audio Conferencing' so that Skype uses Pulse (had to change the sound out option in skype to pulse as well) and the other sound settings to ALSA.  Now skype and Rythmbox can play sounds at the same time so this is a great step forward!!!  Thanks for the tip.  Hopefully this change will resolve all my sound issues.

One thing that is strange is that I have lost my master volume icon in the top right of the screen.  This used to let me set the preferences for mic settings, front boost etc.  How do I get this back or how do I access it in another way?

---

### Post by Airfoot on 2008-11-10
If you reload all of the sound controller programs you are using it should bring back the volume controller icon, if not you might be able to add another one by right clicking an unused portion of your gnome taskbar and selecting "add to pannel..." then scroll down until you see "Volume control" and click "add.."

---

### Post by jf1991999 on 2008-11-10
> **Airfoot said:**
> If you reload all of the sound controller programs you are using it should bring back the volume controller icon, if not you might be able to add another one by right clicking an unused portion of your gnome taskbar and selecting "add to pannel..." then scroll down until you see "Volume control" and click "add.."

Thanks!!!  All fixed and working great now.  Sound levels are actually higher which is good.

---

