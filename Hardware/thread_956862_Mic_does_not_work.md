---
title: "Mic does not work"
date: 2008-10-23
forum: Hardware
---

### Post by dethredic on 2008-10-23
So, I have this old Mic that I want to use to talk on skype, but I can't get it to work.
I go Applications > Sound and Video > Sound Recorder. I tried recording something, then I saved the file and I can't hear anything.
My friends can't hear me on skype either.

It works fine on Windows.

---

### Post by Keenan-Windel on 2008-10-23
I had this problem with Skype. I solved it by right-clicking on the speaker icon in the top right corner of the desktop and selecting "open volume control." There, under preferences, you'll find options to add mic boost, capture, etc. Increase the volume on those and see if that helps.

If that doesn't fix Skype (try soundrecorder first to see if the mic is now working), go into the options menu in Skype and find the audio section ("sound devices"). Change the "Sound In" settings one at a time and see if that fixes it.

It took some fiddling around with volume switches and Skype options, but I eventually got it working.

Note: if you increase the volume on the mic and unmute it, you should be able to hear the input from the microphone. I also changed the "Audio Conferencing" settings in System > Preferences > Sound to Pulse Audio. I don't know if that helped fix it or not, but I was able to hear the output of the mic when I clicked "test."

Regards,

Keenan

---

### Post by pirattrev on 2008-10-23
yeah, same response as Keenan-Windel. Open skype (or audacity) and play around with the sound setting check boxes until it picks something up. for me i had to enable "internal mic" and the "capture" function, plus i had to change the input source to internal mic. However guess and check is the only sure way to solve it because it's such a hardware dependent problem

---

### Post by komoras on 2008-10-24
maybe this will solve your problem:


first set this here so you can see all the options: 
(edit / preferences)

[[IMG]http://i2.photobucket.com/albums/y49/ROSVL/th_Screenshot.png[/IMG]](http://s2.photobucket.com/albums/y49/ROSVL/?action=view&current=Screenshot.png)

then adjust the mic / mic boost to the desired size: 
(max is not recommended because of the possible distorsion but see what is the most convenient)

[[IMG]http://i2.photobucket.com/albums/y49/ROSVL/th_Screenshot-1.png[/IMG]](http://s2.photobucket.com/albums/y49/ROSVL/?action=view&current=Screenshot-1.png)

and set also here the line-in: 
(now it depends on where the mic is pluged-in : in the line-in (blue socket) or mic (pink socket), but set this just in case

[[IMG]http://i2.photobucket.com/albums/y49/ROSVL/th_Screenshot-2.png[/IMG]](http://s2.photobucket.com/albums/y49/ROSVL/?action=view&current=Screenshot-2.png)

check every swich you have:

[[IMG]http://i2.photobucket.com/albums/y49/ROSVL/th_Screenshot-3.png[/IMG]](http://s2.photobucket.com/albums/y49/ROSVL/?action=view&current=Screenshot-3.png)

adjust the input source: 
(line-in or mic / mic it depends in which socket is it pluged-in)

[[IMG]http://i2.photobucket.com/albums/y49/ROSVL/th_Screenshot-4.png[/IMG]](http://s2.photobucket.com/albums/y49/ROSVL/?action=view&current=Screenshot-4.png)

also for the musicians who have distortions when playing instruments 
set the line-in level exactly as mine in order to remove the same 
by that you will get a much clearer sound

---

### Post by dethredic on 2008-10-24
Ok, thanks for the feedback guys. I have made some progress, but I am not quite there yet.

Here is a screen shot of what I had:
[http://img259.imageshack.us/img259/6056/micae1.png](http://img259.imageshack.us/img259/6056/micae1.png)
With this I had my Mic pluged in the pink (mic) spot on my sound card (back of my comp).

I changed the input to from Mic to Front Mic, then pluged the mic into the front of my computer, and it works!!!

So, I would like to be able to keep it pluged in at the back of my computer. Any ideas on how to do this?

---

### Post by komoras on 2008-10-24
> **dethredic said:**
> Ok, thanks for the feedback guys. I have made some progress, but I am not quite there yet.

Here is a screen shot of what I had:
[http://img259.imageshack.us/img259/6056/micae1.png](http://img259.imageshack.us/img259/6056/micae1.png)
With this I had my Mic pluged in the pink (mic) spot on my sound card (back of my comp).

I changed the input to from Mic, then pluged the mic into the front of my computer, and it works!!!

So, I would like to be able to keep it pluged in at the back of my computer. Any ideas on how to do this?

try to set the input source to - front mic
or plug it in line-in and set the input source to line-in

you also have to set the preferences in the software that you are using with your mic

I am assuming that in the skype it's set to default to use the front mic...

---

### Post by dethredic on 2008-10-24
Ok, my last message was a little unclear. I edited it so it now makes sense, so try re reading it.

When the mic is plug in upfront, I tried the test call in skype and I could hear myself, but I was very very very very faint. In the voice recorder I was a good volume though.

---

### Post by komoras on 2008-10-24
> **dethredic said:**
> Ok, my last message was a little unclear. I edited it so it now makes sense, so try re reading it.

When the mic is plug in upfront, I tried the test call in skype and I could hear myself, but I was very very very very faint. In the voice recorder I was a good volume though.

the only thing more you can do with volume control is:
File/Change Device
and put everything everywhere to max level

also
try to adjust the sound level through skype if possible

hope you will solve your problem

I have no more ideas what could it be...

---

### Post by dethredic on 2008-10-25
> **komoras said:**
> the only thing more you can do with volume control is:
File/Change Device
and put everything everywhere to max level

also
try to adjust the sound level through skype if possible

hope you will solve your problem

I have no more ideas what could it be...

Ok, thanks for everything!

---

### Post by komoras on 2008-10-25
np
glad I helped a little

---

### Post by dethredic on 2008-10-25
Ok, I have no idea how I did it, all the settings seem to be the same as last time, but my mic is pluged in back and it works just fine in the sound record. So, that is good news!!!

Now, I open skype, and I try to make a test call and see if the volume is still off, and I get the error message: "Problem With Audio Playback". This didn't happen before. Any ideas how to fix this?

EDIT: The make test sound doesn't make a test sound.
EDIT: I tried all the different "sound out" options, and they didn't help.

---

### Post by komoras on 2008-10-25
maybe it just needed a reboot or alt+ctrl+backspace after the setings


try to turn off any other sound software like xmms vlc audacity etc
8.04 is realy having some audio driver issues...

I never used skype but try in the preferences to put the audio output
for example to OSS

and every other sofware to ALSA

worked for me when playing vlc and xmms at the same time

tough I still have problem with audacity...

just try to play a little bit with thouse setings

---

