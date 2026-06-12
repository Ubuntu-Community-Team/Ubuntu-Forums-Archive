---
title: "sound dissapeared"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by nspattak on 2009-10-27
I have upgraded to 9.10 beta for a couple of weeks now and I have lost my sound.

It used to work and everything appears to be fine except that I do not hear anything.

sound card appears under lspci, it is not muted and I even see applications using the sound server when I try to play sth. however I do not hear anything.

i have tried using mplayer from cli, listening to online videos/music or watching videos locally.

any ideas ?

---

### Post by Claus7 on 2009-10-27
Hello,

what I would advice you is to wait a little, till the final release is out.

If you do not, then you can mess with pulseaudio preferences or alsamixer. This was happening also to me from time to time, while I was making an upgrade since alpha 5. Some configurations seems to change and need to be put back.

Regards!

---

### Post by nspattak on 2009-10-27
This is what I originally thought, but then again it has been like this for almost two weeks and I would like to know what is wrong or even help fixing it. any ideas as to what to check?

---

### Post by Claus7 on 2009-10-28
Hello,

at first open a terminal and type alsamixer.
There you will see many options that you can configure. Do you see any of them being muted? Do you have more than one sound card?
Is the right one chosen by alsa?

Then you could go to Applications -> Sound & Video and choose Pulse Audio Device Chooser.

From there, if you choose manager and then Sample Cache, can you hear any sound? Check out the different options you have in the bottom.

Open firefox or whatever you think can produce sound and check out Volume Control. There in playback see if you have the right configurations. There, if the application has sound, you would be able to see a bar going back and forth, depending on the sound you hear. Also check out the other tabs in this category. 

This is what I can think of by now. Check these out and see. I suppose that they should work...

Good luck,
Regards!

---

