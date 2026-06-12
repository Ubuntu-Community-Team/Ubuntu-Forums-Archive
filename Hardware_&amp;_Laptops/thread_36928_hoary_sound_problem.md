---
title: "hoary sound problem"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by holandapedro on 2005-05-25
Hi,

  I installed Ubuntu, and sound worked fine. But as soon as I use the volume control to adjust volume, the sound vanished. I am using a Via Vinyl AC97 sound card. Any suggestions of what may be happening. Sorry if I am a bit vague, but I am new in Ubuntu/Linux...

Pedro

---

### Post by jkndrkn on 2005-05-25
How have you set up your sound? If you don't use ALSA, then I recommend trying it.
Look here: 

[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

And here: 

[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

---

### Post by MrMunson on 2005-05-25
I'm normally not a very grafically oriented man but I had some sound problems on my computer and I found that switching to ALSA worked it all out. I used the brilliant graphical interface called **Multimedia Systems Selector** under the **System --> Preferences** menu. When loaded, I simply selected ALSA on both **Default Sink** and **Default Source** under the **Audio** tab. Might be a quick'n'dirty fix worth a shot at least before you try on the How-To's.  ;-)

---

### Post by holandapedro on 2005-05-25
Thank's for your messages. Unfortunately the suggestions didn't work... I still don't understand the problem I am having. What exactly happend when I opened the volume control manager, to spoil my sound configuration? I can here that "some" sound is present (a dirty noisy coming out of the speakers). Again, I think it is important to note that the sound was working after Ubuntu's installation (and before trying to set the volume). Thank's again!

---

### Post by MrMunson on 2005-05-27
Hi Pedro!

Sorry to hear non of the tips worked out. 

When you open up the **Multimedia Systems Selector** now, what sound cards do you have under **sink **and **source**? Are these the same as from the install, i.e., you havent touched them or anything?

Assuming the above two settings are indeed as they were in the default install, could  you give a bit more information (if possible) on what you did in the **volume control manager** right when the stuff stopped working? If I can recall right, there is a setting in there somewhere where you can choose what sound device (i.e., card(?)) that you want to adjust volumes for. You didn't change any of that?

As far as my limited experience count's, I much prefer using ALSA cause it seems more reliable and better sounding. Do you just want to get sound back working or do you want to try and get ALSA to work? Stupid question maybe but those are two different approaches to trying to solve the problem I think. 

Hope you can dig up a few more details on the problem. Until then -- have a great weekend!  \\:D/

---

