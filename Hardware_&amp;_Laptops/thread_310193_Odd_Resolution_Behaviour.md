---
title: "Odd Resolution Behaviour"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by freebeer on 2006-11-30
Recently I've noticed that when I turn on my 6.06 box, the screen resolution comes up in 640x480.  I can't change the resolution through System -> Preferences -> Screen Resolution as that is the only resolution offered.

However, if I restart the machine, everything returns to normal (1024x768) at restart and my options are back to normal.

This phenomenon just started recently (last two days).  What might be causing this?

The video is one of those cheapy on-the-motherboard type arrangements.  VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video if that's of any relevance.

Thanks!

---

### Post by styracosaurus on 2006-11-30
Did you upgrade or update anything?

One place to start looking is xorg.conf, I think. There is a section that lists resolutions, although if you can get back to what you want by rebooting I am not sure if this will be any help. Post it though, it can't hurt!

Maybe someone who knows more than I do can decipher it when you do.

PS xorg.conf is /etc/X11/xorg.conf, you should be able to read it with any text editor as normal user.

---

### Post by freebeer on 2006-11-30
Thanks.

I had a look at the xorg.conf file and it listed the different resolutions.  But I wouldn't have expected otherwise, as this was after the restart.  :)  Once restarted, it defaulted to the higher resolution.

I suspect what's happening is that perhaps from a cold start, my video isn't being detected right away, or it's being detected improperly.  I'll have to watch the boot sequence closly next time to see if I get any errors.  On restart, the board is warm enough (or whatever) that on the second attempt it finds it.  But that would be rather strange... and it this behaviour is rather new.

I don't think I've changed any setting, but I have downloaded and installed some new software and/or updates.  I don't think there was anything in that group that might have fiddled with the graphics settings but you never know. ;)

---

### Post by styracosaurus on 2006-11-30
Hmm I'm not sure then. The board warming up sounds a little strange though, I don't think that is the issue, I have never heard of that. But I could be wrong!

---

### Post by freebeer on 2006-12-01
Yeah.  It's rather weird.  Not a biggie though.  For the record, it didn't happen today when I turned on the machine.

---

### Post by Stenico on 2006-12-04
I too experience this behaviour (Edgy Eft). After restarting my machine X is often at an incorrect (lower) resolution.

I solve this very easily by pressing Ctrl-Alt-Backspace which restarts the X server, which always then comes back up at the correct resolution.

I also have this bug on an installation of Arch linux on the same machine, so I assume it is an Xorg bug rather than a Ubuntu bug.

---

### Post by freebeer on 2006-12-05
Nice to know it's not just me.  :D

For the record, it hasn't happened in a few days.  *shrugs*  It's not that it's annoying or bothersome to change - I was more interested in knowing ***why*** it was doing it.

---

