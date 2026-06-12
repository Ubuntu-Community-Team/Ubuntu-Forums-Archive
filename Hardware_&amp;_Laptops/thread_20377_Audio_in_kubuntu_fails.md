---
title: "Audio in kubuntu fails"
date: 2005-03-16
forum: Hardware &amp; Laptops
---

### Post by wbeck85 on 2005-03-16
I just installed kubuntu-desktop via synaptic. I think it, for the most part, looks very nice. I like KDE.

However, I have two problems. The first is with the audio. It has problems. I get this message on logon (of kde)

"Informational artsmessage <2>

Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (No such file or directory)
The sound server will continue, using the null output device."

It does not happen when i boot into the original gnome.

THis happens when using ALSA. I tried OSS and got a similar message:

"Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such device)
The sound server will continue, using the null output device."

Why is this not working in KDE?

I have a sager np4750 laptop with onboard AC97 audio.

---

### Post by wbeck85 on 2005-03-16
The sound is apparently not working in gnome either. i guess i screwed something up in the kubuntu install. that makes me sad. does kde have its own audio controller or something that would be conflicting with my original sound setup (which worked very well by the way) ? I'm using hoary 5.04 i396 version (despite my amd64 processor).

---

### Post by wbeck85 on 2005-03-16
Another weird thing is that audio files (mp3, cd audio, avi and DVD) all play in totem-xine, but when i try to play them in Realplayer10 or xmms (not the avi and dvd, of course) i get an error saying "(in xmms) Please check that: Your soundcard is configured properly, You have the correct output plugin selected, No other program is blocking the soundcard" and "(in Realplayer10) Error, Cannot open the audio device. Another application may be using it."

And i have closed totem when I try to use the other media players. Weird. xmms was working just before the kubuntu-desktop install.

---

### Post by Zepp on 2005-03-19
I am having the same problems :(

---

