---
title: "Inverting second screen (NVIDIA)"
date: 2010-01-31
forum: Hardware
---

### Post by Kivech on 2010-01-31
Hi all,

After some time I came back and installed Ubuntu. It's been a while, so I'm a bit rusty still and am running into some practical problems.

One of which is my second monitor. I use this to play movies while I work behind my PC. It has one BIG downside: it is hanging upside down. So I need the image displayed on that monitor to be inverted.

Now, I followed through all the steps of [this]("http://ubuntuforums.org/showthread.php?t=478244&highlight=rotation+dell") thread. 

Unfortunately it doesn't seem to be working for me at all. When manually editing xorg.conf, it just ignores the Option "Rotate" "INVERT" line, and when I do it through the nvidia settings tool it just resets at every reboot.

Does any of you know how to get these settings persistant so that every time I boot my system the image on the second monitor is inverted?

Any help will be highly appreciated.

---

### Post by jharder01 on 2010-01-31
As for keeping your settings consistent from boot to boot, try 
```
sudo nvidia-settings
```
from the terminal.  After you've made your changes click "Save to X Configuration File."

If you get an error, you'll need to google it.  There's a thread out there somewhere that explains the steps needed to allow it to save.  Its something easy, but since I can't remember you're probably better off finding it first hand.

---

