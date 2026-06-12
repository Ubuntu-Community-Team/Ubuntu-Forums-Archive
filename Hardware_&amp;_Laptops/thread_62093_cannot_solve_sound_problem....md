---
title: "cannot solve sound problem..."
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by one_ro on 2005-09-03
Dear listers,

I have a problem with my sound card in Kubuntu running on a Toshiba Sattelite Pro laptop. I tried all sorts of things but with no avail. Compiling the latest alsa drivers did the worst, now I get this error from the very start:

"Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device."

The command alsamixer gives the following error:
"alsamixer: function snd_ctl_open failed for default: No such file or directory"

The command lspci gives:
"0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)"

I don't seem to find a sound module when typing lsmod (if needed, I could copy and paste the whole result).

Any hint would be highly appreciated.
TIA,
Adrian

---

### Post by MrJack on 2005-09-03
You first need to find and install the kernel module for your sound card and then we can see about alsamixer (and i don't know what module that is , i've searched thow )

-------------------------------------info on laptop:
[http://nicolas.bettenburg.free.fr/linux/](http://nicolas.bettenburg.free.fr/linux/)

Si mult noroc..

---

