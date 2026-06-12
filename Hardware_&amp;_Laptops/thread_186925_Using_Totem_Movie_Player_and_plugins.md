---
title: "Using Totem Movie Player and plugins"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by acupuncter on 2006-06-02
I have an old HP Pavilion laptop and with Ubuntu when I want to play a Real Player video clip I get a message "no decoders...may need to install corresponding plugins.  Which plugin are these?  Are they specific to Ubuntu, although I can't be sure because I'm having trouble playing with video in Windows though I have sound.  Advice?

---

### Post by meng on 2006-06-02
Options include (depending on what type of media files you wish to play, I know they include RealPlayer but you may have others too):
- Install RealPlayer
- Install totem-xine (this will replace totem-gstreamer which I'm guessing is the one installed on your system)
- Install w32codecs and then mplayer (from multiverse repositories)

More details are in the restricted formats wiki. [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

