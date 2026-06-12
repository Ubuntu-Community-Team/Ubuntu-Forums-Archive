---
title: "Oversized resolution / unable to change"
date: 2008-06-30
forum: Hardware
---

### Post by YopY on 2008-06-30
Ohai,

I'm currently trying to install Xubuntu ('cause it's lightweight) on my laptop, and it's on there allright, no problems there. However, the resolution is set to a value higher than my screen is, meaning that the left and bottom of the screen is cutoff. Changing the resolution isn't possible (just sticks to 'default'), and as such, I can't properly use the whole thing.

I figured it would figure itself out once I installed it properly, but sadly, it didn't.

So, how do I fix the resolution business? I'm not sure what the native resolution of the screen is, but it's a widescreen thingy of something like 1280 or ~ish wide, if I remember properly.

Also, occasionally the screen just seems to blank out, after which I have to move a window all over the screen (forcing a redraw of that particular section or something) in order to fix it. Is that related or...?

Also, and this is probably because I can't see the right side of the screen, I can't access the innernets from my laptop (yes, I'm pretty sure I configured it properly through the network connection thingy), so installing new business probably isn't an option, depending on whether you need the right-hand side of the screen to fix that.

So, any solutions? I've tried the stuff found in [this](http://ubuntuforums.org/showthread.php?t=83973) thread, but to no avail - either I'm doing it wrong, or that just doesn't apply to me.

According to the results from lspci (as suggested in some other thread), my VGA compatible controller is a "VIA Technologies UniChrome Pro IGP (rev 01)" It doesn't display the horizontal / vertical refresh rates as indicated though, instead it goes 'edidfail'. Read some bug about that, which suggested using get-edid, but while it does (seem to) return my graphics card (or something), it doesn't supply me with any data.

Small update, I've found a xorg.conf file for a similar system that I have, but that doesn't work either. It defines a horizontal / vertical synch, which leads to a list of resolutions in the configuration options (with weird refresh rates btw), but not one of them works properly.

So, any idea how I can fix this? Will it work if I threaten to go back to Windows, which works out-of-the-box lyk z0mg? Help would be much appreciated. Xorg's auto-config thingy doesn't seem to detect my hardware (neither graphics chip nor monitor), so that isn't helping either.

---

