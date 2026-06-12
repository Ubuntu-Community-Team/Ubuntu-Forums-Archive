---
title: "Kubuntu livecd"
date: 2009-08-05
forum: Hardware
---

### Post by dotnick on 2009-08-05
With the release of KDE4.3, I decided to try it out last night on the nightly build.  

My test hardware:
HP Mini 1035NR Netbook

With Kubuntu, my wireless networking is NOT automatically configured with the correct modules loaded (and I don't even know which modules need to be loaded).  However, with Ubuntu, the opposite is true.  Why is it the gnome version detects and loads the correct wireless module, but the kde version does not?

Secondly, the sound seems to work now.  I'm assuming that's due to the tremendous work of the ALSA devs.  I am hearing the speakers pop occasionaly though, even when the audio is muted.  Any ideas on that one?

---

### Post by slakkie on 2009-08-05
To figure out what kind of network card you're using:

lspci

---

