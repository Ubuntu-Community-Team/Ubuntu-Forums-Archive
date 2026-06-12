---
title: "Realtek HD audio drivers issue - Roll back to previous? - 8.10"
date: 2008-11-04
forum: Hardware
---

### Post by Silverspell on 2008-11-04
Dear all,

Acer Aspre 5672AWLMi
Ubuntu 8.10

I am quite an unexperienced linux user. Recently i was trying to get my microphone and sound to work -after upgrading to 8.10- i finally made it happen. The drivers i was using where the ones provided by the Ubuntu installation (HDA Intel). At the meantime i was downloading the official Realtek drivers for Linux, which i had the (unfortunately bad) idea that they would probably make my life easier and decided to install them. Well this, was the beginning of the end. I have no sound now, and i cannot seem to find a way to "roll-back" to the previous drivers i was using.

Symptoms:
-No sound input/output
-When i try to access Volume control i get the message "No volume control GStreamer plugins and/or devices found."
-My soundcard is detected from Ubuntu.

Questions:
-Is there anyway to roll back to the previous drivers?
-If not how can i completely remove the realtek ones and then purge/reinstall alsa drivers?
-Any other ideas/suggestions?

---

### Post by Silverspell on 2008-11-05
A small update:

My second kernel works fine (has the previous sound drivers and sound is working perfectly).

Is there a way to "transfer" settings from one to the other? What i am trying to avoid here, is a reinstallation of the whole OS for a sound card driver issue in one of the two kernels.

Thanks

---

### Post by pheonixxiii on 2008-11-25
Silverspell, I'm in _exactly_ the same boat that you are in. I've been trying to figure it out for a few days, and I haven't had much, well honestly, any luck whatsoever.

I'll post back If I find anything of value.

---

### Post by Silverspell on 2008-11-26
Hey phoenix,

Sorry to hear that man. I actually eventually reformated the whole thing, since my laptop had a whole other bunch of issues (Which i still haven't figured out all of them...:P). Anyway, i wish you luck, and if i run up to anything usefull i'll post it here.

Well if you manage to fix it though, i'd like to know how you did it.

Good luck.

---

