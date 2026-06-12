---
title: "Skype help - My make or break app"
date: 2008-10-23
forum: General Help
---

### Post by Crusader_Tech on 2008-10-23
Hello everyone, and thank you ahead of time.

Skype is the ONLY app keeping me from switching my office computer to 100% Ubuntu. 

On 2 separate computers, I have installed Skype in Ubuntu 8.10, but I have had no success in getting it to function. 

I go to [www.skype.com](www.skype.com), download the installer for Ubuntu, and install it successfully. However, when I try to make a test call, initially it always fails do to an audio problem. When I go into the audio properties, there are LOTS of choices for sound output and input. After trying several, the closest thing I can get to is choppy sound, but still no sign of my mic working.

I also can't seem to get skype to recognize my creative webcam. 

As I said, this is the one app keeping me from thrusting Windows Vista from my desktop. Any help is greatly appreciated.

---

### Post by Ameneon on 2008-10-24
One thing that you might want to check (it's really quite obvious so you might actually have checked it) is the input volume (not in skype but in the mixer app itself). Perhaps this is now changed but when I tested setting up skype first I first had to find the right alternative for input/output and then adjust the input volume quite high (getting close to causing feedback from the loudspeakers as the input is being fed through regardless of whether an application such as skype actively awaits input or not).

Once that was solved I could hear and be heard, although I had only mediocre luck with my webcam, a logitech pro 5000. Video starts but is way way too dark, checking with ekiga or amsn doesn't provide a watchable picture even at the brightest setting, only way to solve this would be to set a really bright light facing myself, which isn't an alternative. So at the moment I do without the video calls, but this is something I too look to get working at some point. I do not know how to make skype recognize the webcam though, if it doesn't already..

---

### Post by markbuntu on 2008-10-24
I wrote a guide for getting skype to work with pulseaudio which is the default sound server for hardy 8.04 and intrepid 8.10:

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

Let me know if this works for you. It works for sure on 8.04.

---

### Post by whitethorn on 2008-10-24
I use a logitech quickcam pro 9000 it works in skype and ekiga.  It hangs sometimes, I then just need to unplug it, plug it back in, it then works fine (only hangs once I don't know why)  Oh and the quality of the video is pretty good. Anyway to get it to work with pulseaudio I followed this guide.  Worked like a charm for me.

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

