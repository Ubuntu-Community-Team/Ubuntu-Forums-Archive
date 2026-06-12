---
title: "Cannot run multiple sounds at the same time :("
date: 2008-05-07
forum: Hardware
---

### Post by ownaginatious on 2008-05-07
I'm having a problem where I am unable to have more than one application at a time producing sound. This is a problem, because I like to play music while I play games. I'm using Hardy Heron. Does anyone know how to fix this?

My audio controller, according to the lspci command in terminal is:

```
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)

```

Thanks!

---

### Post by hvthao on 2008-05-07
Try to use ALSA output module for all music application. You can configure it in the application preferences. For ex., 
XMMS : Options -> Preferences -> Audio/Video Plugins -> Output Plugin
Audacious: Preferences -> Audio -> Current Ouput Plugin
...
Don't use OSS driver cause' it will occupy the sound card. Of course, your game must be configured to use alsa driver too.

---

### Post by psychofish25 on 2008-05-08
thanks, how do i use it with vlc?

---

### Post by hvthao on 2008-05-08
VLC: choose Preferences
- Stick in Advanced Options (in the bottom of dialog)
- In the left, choose Audio -> Output modules: select Alsa Audio Output in the right column option "Audio Output Module"

---

### Post by psychofish25 on 2008-05-08
> **hvthao said:**
> VLC: choose Preferences
- Stick in Advanced Options (in the bottom of dialog)
- In the left, choose Audio -> Output modules: select Alsa Audio Output in the right column option "Audio Output Module"

hm thats what i did, yet Pidgin is still not making sound.

---

### Post by hvthao on 2008-05-09
My audio card is: 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02).

If your sound system is not working right, i think it is a problem of the driver for the new sound card ICH9 Family.

---

