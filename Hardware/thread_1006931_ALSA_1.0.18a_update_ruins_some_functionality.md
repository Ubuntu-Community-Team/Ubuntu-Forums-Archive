---
title: "ALSA 1.0.18a update ruins some functionality"
date: 2008-12-09
forum: Hardware
---

### Post by CJay554 on 2008-12-09
I managed to fix a sound problem with the Acer 6920 by installing a newer version of the ALSA driver. Thread link: [http://ubuntuforums.org/showthread.php?t=921637&highlight=cjay554](http://ubuntuforums.org/showthread.php?t=921637&highlight=cjay554)

Anyway, one problem did arise from this (which might be why ubuntu comes with an earlier version of the ALSA drivers)

My camera will not work, it was recognized without any driver installations, straight from the box. But after the installation of the ALSA driver it has stopped responding, others have had the same problem with through this method. (May be caused by a driver conflict?)
[ADD]
CAMERA WORKS! but only through cheese's 160 x 120 resolution, otherwise it doesn't work, and it seems very pixilated (because of resolution)

I tried to use EasyCam to install the driver (worked when i had Gutsy and Feisty) but this time it did not detect a camera at all. (Bios conflict?)

My CineDash touch pad (pretty much "fn" shortcuts on the side of the laptop) have been corrupted, before they would work normally and raise the volume, now they do not respond (at least the volume up/down play, pause, forward, etc still work) (Alsa may not be identifying the shortcut keys?)

In the keyboard shortcuts it recognizes my up/down volume as: XF86AudioRaiseVolume, XF86AudioLowerVolume respectively. But does not respond when pressing button, i can change these shortcut keys to any button on the keyboard and they work fine, maybe alsa doesn't support this type of character request?

Also for some reason if i leave my laptop running over night (usually to download/seed torrents) in the morning the screen is down (through power save) but the computer itself is crashed. my caps lock button and my wifi blinking button both blink vigorously and the computer will not respond. I haven't had this problem until i installed the ALSA driver 

In terms, we were able to get sound for a small sacrifice, so i started this thread as a start to troubleshoot these problems. If anyone has any ideas or suggestions to help please do! I REALLY want to get ubuntu working flawlessly with this smexy computer =]

---

### Post by CJay554 on 2009-03-02
UPATE: It isn't the alsa driver that is effecting my system actually as i tested. It is some package that is being updated after a clean installation.

---

