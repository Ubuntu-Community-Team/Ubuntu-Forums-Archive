---
title: "New Monitor causing problems"
date: 2009-12-24
forum: Hardware
---

### Post by ctxt on 2009-12-24
I am having a problem with my Ubuntu install (9.10) after replacing my monitor. It will no longer boot but just stop after the grub until i connect up the old monitor. If i then hook up the new monitor it will work however the picture does not fill up the screen. Can anyone help? I can't be without my linux or else I will break my windows.

Thanks

---

### Post by taurus on 2009-12-24
Looks in System -> Preferences -> Display to see if you can adjust the resolution of your new monitor.

---

### Post by ctxt on 2009-12-26
I have tried that and after getting it to the proper resoultion it still doesn't fill up the screen, also when I use the new screen after changing the resolution it still will not boot to my login.

---

### Post by efflandt on 2009-12-27
Let me guess, you are using DVI or HDMI.  For some reason usplash has issues with digitally connected monitors that do not natively match the resolution in /etc/usplash.conf, even if the monitor is actually capable of the set resolution.  So you can either correct /etc/usplash.conf to the native resolution of the monitor, or (especially if you use different monitors) remove the word "splash" from GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" in /etc/default/grub.  Then do **sudo update-grub**.

For example when I switched from 1280x1024 display that worked fine VGA or DVI to 1280x720 HDTV connected with DVI it worked in its native resolution just logging out of X and back in.  But when I booted later, after the grub2 menu, I got a blinking cursor for a few seconds, then nothing (no disk activity indefinitely).  But recovery mode or manual grub2 commands worked, and it worked when connected with VGA.  Not sure why usplash is so particular about only accepting a native resolution when digitally connected (which should communicate all possible resolutions).

---

### Post by ctxt on 2009-12-28
Thanks I am on Vacation right now, but the moment I get back I shall try it and get back to you. So far that sounds like the most logical explanation, so thanks before hand

---

