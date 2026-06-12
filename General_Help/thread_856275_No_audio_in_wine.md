---
title: "No audio in wine"
date: 2008-07-11
forum: General Help
---

### Post by scottws on 2008-07-11
I just tried to run Starcraft through wine after a pretty long hiatus.  Previously it worked adequately except that I could not play it fullscreen because there were a few big black bands over the top of it, but i could play it fine in a tiny 640x480 window.  The last time I used it was when I was using Kubuntu 7.10.

Now I have Kubuntu 8.04 (simple upgrade) and I just tried to play it again.  I have discovered that fullscreen works fine now, but there is no audio!

It seems this has something to do with pulseaudio.  Wine's wiki says to disable it.  But I don't know how to do that.  I've seen lots of messages saying under Ubuntu to go to System | Preferences | Sound and make sure ALSA is set for everything, but I don't have Ubuntu, I have Kubuntu.

I have gone to System Settings | Sound System | Advanced and set ALSA under "Select Audio Device" instead of "Autodetect," but this has no effect.  I can not find any configuration settings or file for pulseaudio except for /etc/pulse/client.conf, which has every single thing commented out in it.

I saw something that said to use the padsp command to run wine, and use the OSS driver to make it work, but I still had no sound using these instructions.

Does anyone know how to make audio work in wine in Kubuntu 7.10?

---

### Post by diaa on 2008-07-30
According to the comments, the following guide makes audio work with starcraft:
[Make Wine and PulseAudio get along]("http://blog.paulbetts.org/index.php/2007/05/27/make-wine-and-pulseaudio-get-along/")

---

### Post by scottws on 2008-07-31
I should have updated this thread.  A few days after posting this, Adept Updater told me there was a wine update.  After installing that, the sound worked again.

Thanks anyway.

---

