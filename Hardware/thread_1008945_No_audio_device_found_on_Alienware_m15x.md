---
title: "No audio device found on Alienware m15x"
date: 2008-12-12
forum: Hardware
---

### Post by unixSoto on 2008-12-12
I recently installed ubuntu through wubi on an Alienware m15x. I'm a serious beginner to the whole Linux thing, so even though I tried some things already mentioned around here on the forums, I couldn't fix my problem.

Basically, I have no sound. When I double click the Volume Control, it shows the following message :


No volume control GStreamer plugins and/or devices found.


Going through System > Preferences > Sound, in the Device tab, in all options, it says: "(Not connected)".

The lspci cmd gives this for audio device:
 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Any help would be appreciated. Thank you.

---

### Post by unixSoto on 2008-12-12
Bump 
Any help?

---

### Post by unixSoto on 2008-12-13
Help!

---

### Post by Max Payne 2k8 on 2009-07-11
I am curious for an answer too. Please help. I'm not a noob to Linux, but I just can't find the right package for this driver to be compatible with Ubuntu.

---

### Post by Max Payne 2k8 on 2009-07-11
i'm sorry for the quick bump but a quick answer is necessary please

---

### Post by Earthen on 2009-09-26
The audio is there but it only works with the head set by default. It's because the audio out can have many different outputs depending on what you plug in. and I don't think that there are any driver that support this function as of yet. anyway To make sound work alienware m15x, just add this line to the end of /etc/modprobe.d/alsa-base
options snd-hda-intel model=3stack-6ch-dig

then do a restart all should be fine

good luck!

---

### Post by Schuby007 on 2010-11-03
Did that fix the problem?

I have an m15x and I'm running 10.04 and I have no problem with sound through the headphones jack. I've heard that some people can't get the built in speakers working, I have no need for that so I haven't checked.

It could also be a problem with WUBI??

---

