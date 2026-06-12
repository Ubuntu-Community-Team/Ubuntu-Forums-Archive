---
title: "Sound driver help"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by rveska on 2007-12-27
Hi there,

I'm quite new to Ubuntu and Linux in general. I had no sound on my laptop, and according to the manufacturer it was because I had to update my ALSA-module; which of course I tried to do...

Now however, I have only half the sound driver installed, i.e. I've got no units to control the sound volume, so my laptop is always on mute.

Hopefully this could be fixed by installing the required software/what-ever, but I don't know which and how!

Can someone help me finding the right software and give me some instructions on how to install it, OR tell me how to completely reinstall all of my soundcard software, -driver etc.???

Thanks
[INDENT] -Rasmus[/INDENT]

---

### Post by Casual Fan on 2007-12-27
Oooh! Oooh! Another chance to post a link to my favorite thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I'm sure this will help.

CF

---

### Post by Yellow Pasque on 2007-12-27
It might help to know what laptop and sound device you have. If unsure, run
```
lspci | grep Audio
```

---

