---
title: "Samson G-Track Condenser USB Mic Help"
date: 2009-10-10
forum: Hardware
---

### Post by chad724 on 2009-10-10
Hi guys,

I can't seem to figure out how to get my Samson G-Track Condenser USB Microphone working in Ubuntu. In Windows, you just plug it in and it works. Not so with Ubuntu.

Is there any software I need to download?

Thanks,
Chad

---

### Post by chad724 on 2009-10-10
Sorry about the original post, I'll make some use out of this thread.

Upon Googling, I couldn't find anything, so I posted here, but I was searching some more and found out how to get it to work.

First, make sure you have everything updated involving sound management:
> sudo apt-get install asoundconf-gtk alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras
Then it is a matter of going to System -> Preferences -> Sound and choosing "USB Audio Codec USB Audio (ALSA)," under Audio Conferencing -> Sound Capture. Click "Test" to test out the microphone.

Sorry again for the post without Googling long enough!

---

