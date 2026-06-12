---
title: "Android tablet as second display for laptop using VNC"
date: 2016-04-27
forum: Hardware
---

### Post by Fringilla on 2016-04-27
I have an older Android tablet and I want to use it as a secondary display for my laptop with Peppermintos 6 (derived from Ubuntu 14.04 with LXDE) with VNC.
Because no side of tablet screen matches my laptop screen (laptop: 1280x800; tablet: 1024x768) I cannot simply stretch the resolution as recommended in various forum threads.


So I found this solution ([http://askubuntu.com/a/750497/525917](http://askubuntu.com/a/750497/525917)) and tried to follow the steps.


Unfortunately Xrandr doesn't know any virtual output, so I can't add any mode to it. I wanted to create a xorg.conf file which is not used now but should override default settings. Because X -configure in recovery mode ended with error, I created xorg.conf with only desired virtual screen section in it and hoped the rest would be taken from usual default settings. It wouldn't.


Then I tried to use some existing output (VGA-1 or DP-1) to do the same thing. But 
```
xrandr --output VGA-1 --mode 1024x768_60.00 --left-of LVDS-1
```
failed, probably because VGA-1 (or DP-1) is physically disconnected and Xrandr knows about it.


After that creating VIRTUAL output somehow seems to be the right way again, but I don't know how to do it. The tutorial I followed works for the author and some other people so it should be possible. Any advices, please?


P. S: I use default noveau driver, solutions using driver from nVidia are not possible for me because of persisting ACPI problems.

---

