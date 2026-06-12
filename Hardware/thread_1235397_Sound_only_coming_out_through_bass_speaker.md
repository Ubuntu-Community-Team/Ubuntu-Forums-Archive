---
title: "Sound only coming out through bass speaker"
date: 2009-08-09
forum: Hardware
---

### Post by Veinor on 2009-08-09
I have a MSI GT725, which as a subwoofer as well as the normal speakers. The problem is that on my Ubuntu 9.04 install, the sound **only** comes out through the bass speaker, so it sounds distorted. This happens on the 9.04 LiveCD as well. Copies of the outputs of lspci -vv and aplay -l are attached. I've tried changing the preferences in System->Preferences->Sound to no avail, and the settings in the Volume Control applet. I could really appreciate some help!

---

### Post by Veinor on 2009-08-09
Oh, the sound also keeps playing through the speakers when I plug in headphones (which sound like normal)

---

### Post by ZaHACKieL on 2009-08-09
I had a weird problem with sound once. I got sound through the speakers only when I selected the "Headphone as Line Out" option in the alsa-mixer in Ubuntu 8.10. But the sound started working erratically, sometimes it was working fine and suddenly stoped working for some seconds or minutes, whatever.

I finally discoverd that I actually had 2 problems, a hardware problem and a software problem.

The hardware problem was the card that has the headphones and microphone ports had a malfunction.

The software things was a bug that made the speakers sound when you connect the headphones.

So, I'm telling you this so you can consider the option that you may have 2 problems. Did you try your speakers in windows or other OS? that could discard a hardware problem I guess.

About the speakers working even when you connect your headphones take a look here:

[http://ubuntuforums.org/showthread.php?p=4869649](http://ubuntuforums.org/showthread.php?p=4869649)

Let me know what happens

---

### Post by Veinor on 2009-08-09
The sound works fine in Windows 7, so the hardware is good. I'll try that link you posted for the headphone issue.

---

