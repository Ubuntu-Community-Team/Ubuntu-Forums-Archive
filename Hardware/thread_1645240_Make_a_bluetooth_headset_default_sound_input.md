---
title: "Make a bluetooth headset default sound input"
date: 2010-12-14
forum: Hardware
---

### Post by jambel on 2010-12-14
Hi,

I make my bluetooth headset to pair automatically but I can't use it until I open sound preferences and select it from sound input tab (I only need to use the microphone).

Is there any way to be selected when headset is connected?

I use Ubuntu 10.10

Thanks!

---

### Post by efflandt on 2010-12-14
I have been thinking about trying to figure out how to automate that for some time.  You might get some insight from this thread [http://ubuntuforums.org/showthread.php?t=1370383&highlight=headset+audio](http://ubuntuforums.org/showthread.php?t=1370383&highlight=headset+audio)

That may not be automatic, but at least you can do it with a hot key, or desktop or panel launcher with key press or mouse clicks. Although, if you just want to use it yourself, you do not necessarily need to put the script in /usr/local/bin.  If you **mkdir bin** in your home directory, the next time you log in that would automatically be in your PATH.  So you can put your own scripts there (no need for sudo to edit or put them there).

---

### Post by jambel on 2010-12-15
Great, thank you!

I'll try this when I get back home!

> **efflandt said:**
> I have been thinking about trying to figure out how to automate that for some time.  You might get some insight from this thread [http://ubuntuforums.org/showthread.php?t=1370383&highlight=headset+audio](http://ubuntuforums.org/showthread.php?t=1370383&highlight=headset+audio)

That may not be automatic, but at least you can do it with a hot key, or desktop or panel launcher with key press or mouse clicks. Although, if you just want to use it yourself, you do not necessarily need to put the script in /usr/local/bin.  If you **mkdir bin** in your home directory, the next time you log in that would automatically be in your PATH.  So you can put your own scripts there (no need for sudo to edit or put them there).

---

### Post by jambel on 2010-12-16
I test it but I can only change the output and not the input which I really want.

When I run pacmd set-default-sink "bluez_sink.XX_XX_XX_XX_XX_XX" it changes only the output device. I don't want to change the output, only the input

Any other ideas? Is there any way with pacmd or pactl to change only the input device?

Thanks

> **efflandt said:**
> I have been thinking about trying to figure out how to automate that for some time.  You might get some insight from this thread [http://ubuntuforums.org/showthread.php?t=1370383&highlight=headset+audio](http://ubuntuforums.org/showthread.php?t=1370383&highlight=headset+audio)

That may not be automatic, but at least you can do it with a hot key, or desktop or panel launcher with key press or mouse clicks. Although, if you just want to use it yourself, you do not necessarily need to put the script in /usr/local/bin.  If you **mkdir bin** in your home directory, the next time you log in that would automatically be in your PATH.  So you can put your own scripts there (no need for sudo to edit or put them there).

---

