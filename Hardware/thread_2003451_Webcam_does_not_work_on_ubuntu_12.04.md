---
title: "Webcam does not work on ubuntu 12.04"
date: 2012-06-14
forum: Hardware
---

### Post by gugu88 on 2012-06-14
Hi there,

about a week ago I installed Ubuntu 12.04 on my personal computer, everything works just fine except the webcam. I have two different webcams, one really old Logitech and the other a bit newer Trust both of them with the integrated microphone. 

I tried to follow several different guide and threads in order to fix this problem, but without any success!!!

In particular the Logitech's webcam does not work at all, the Trust's webcam works the video but even after a lot of try the microphone (the most important part!!!) does not work either with skype or sound recorder.

The audio settings seem to be all right  either on pulse audio control and on alsamixer!! I do not know what to do anymore!!!

On windows xp both the webcams work perfectly with any software (skype, sound recorder and video recorder).

Any help will be appreciate!!

Thanks

---

### Post by ajgreeny on 2012-06-14
Are you certain that the mic is not muted?  I have been caught out with this in the past using alsamixer in terminal where the levels appear high enough but the slider shows MM at the bottom for a muted channel.  Just hit "m" if so and the mute will be toggled on/off.

Apologies if you know this and have checked, but I see you are a new forum user, if not a new Linux user.

---

### Post by gugu88 on 2012-06-14
Yes I checked every microphone channel!!! None of them is mute. The weird thing is that I have not a channel **Mic **in my alsamixer but just **Front/Rear mic **and **Front/Rear mic boost**. Anyway I tried any possible combination of volume without success!!!

Furthermore in the PulseAudio Volume Control the microphone is seen in the sheet **Imput devices**!!!

In attach there are two pulse audio control's screenshots, one about **Imput devices** sheet and the other about **recording** sheet while I'm using **Sound Recorder**. 

(anyway I'm quite new as linux user so you can try also simple solution even if I already try a lot of possibilities seeking on internet and on the italian forum!!)

---

### Post by ajgreeny on 2012-06-14
On your first screenshot you show line-in as the capture device (the lower slider), not the Mic, which I suspect it should be.

Open alsamixer again in terminal and use tab to go to "Capture" page.  Move the active item to Mic and hit spacebar to activate the capture with the Mic.

Good luck.

---

### Post by gugu88 on 2012-06-14
I think I have already tried also this strategy!!! If I go to the capture page in alsamixer I have **Capture **and **Capture 1**, I think they are associated with **Input source **and **Input source 1**. For what concern the channels Input source I can choose among **Front mic**, **Rear mic** or **Line in**. I've already tried different combination trying to activate and deactivate the various channels but the mic still doesn't work. 

I send you the alsamixer screenshot of the capture page. Now there are this setting but I've already tried almost every possible combination!!!!

I'm sending you also two alsamixer's screenshots showing what appears if I press F6 and I select **USB Device**, It appears that capture bar with written **mic** on  the bottom and if I press tab shifting to Playback sheet It appears that message I don't understand!!

---

### Post by gugu88 on 2012-06-14
This is weird, isn't it??? Playback control shouldn't be the one used in order to control the actual volume???

---

### Post by gugu88 on 2012-06-15
Then................................................ nobody can help me???????????????

I don't know what to do anymore!!!!!!!!!!! :confused: :confused: :confused:

---

