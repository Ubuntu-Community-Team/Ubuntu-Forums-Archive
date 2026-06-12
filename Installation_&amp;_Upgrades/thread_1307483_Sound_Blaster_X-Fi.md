---
title: "Sound Blaster X-Fi"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by seanj on 2009-10-31
I'm going to try here for help, then I give up on Ubuntu. I asked people on IRC for help, but no one had an answer. Someone even blamed my hardware configuration for the problem, when this sound card works on Windows and every other GNU/Linux distro I've tried recently.

Sound Blaster X-Fi. Line-in does not work at all with ALSA or OSS.

Sorry for my anger, but I don't understand why you guys would release an OS that only works for half the people who try it.

---

### Post by apirec on 2009-10-31
Well, first of all, I am not one of the guys who released this OS, and I doubt that they're reading much of this forum.
But to stay in your manner of speech: It only runs in Windows because you have the right drivers installed! Did you make sure that you're running alsa 1.0.21 which claims to be the first version supporting the X-Fi?

---

### Post by seanj on 2009-10-31
No, it looks like the version of ALSA is one step behind the latest... I assumed it was the correct driver because PCM was working. I don't exactly know how to install a new ALSA, but I was able to install and configure OSS, and even then the line-in jack did nothing.

---

### Post by cascade9 on 2009-10-31
you could try the creative linux drivers. I would link you straight to the page, but theres a lot of X-Fi's around, so its probably best to start here-

[http://support.creative.com/Products/Products.aspx?catid=209](http://support.creative.com/Products/Products.aspx?catid=209)

Click on the version you have, scroll down to 'latest downloads', get the Linux 32 bit / 64 bit Driver, download, install.

---

### Post by seanj on 2009-10-31
Thanks.

---

