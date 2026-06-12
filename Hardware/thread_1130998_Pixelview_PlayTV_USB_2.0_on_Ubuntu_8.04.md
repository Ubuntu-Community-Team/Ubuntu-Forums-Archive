---
title: "Pixelview PlayTV USB 2.0 on Ubuntu 8.04"
date: 2009-04-20
forum: Hardware
---

### Post by Fisher on 2009-04-20
Hello. I just get a Pixelview PlayTV USB 2.0 capture card, it works fine in 8.10, but did not on 8.04.
Does anyone knows why?
Thanks!!

---

### Post by Fisher on 2009-04-20
Found almost all I need here:
[http://ubuntuforums.org/showthread.php?t=460214](http://ubuntuforums.org/showthread.php?t=460214)
But, to get sound in tv time, i need to open a shell and type:
sox -r 48000 -t alsa hw:1 -t alsa hw:0
Is there a way to associate the alsa hw:1 to one unused mixer channel??
Thanks!!

---

