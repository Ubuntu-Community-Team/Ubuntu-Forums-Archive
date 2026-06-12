---
title: "P105 Satelite Sound Issue Un-resolved please help"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by mbaker1965 on 2007-10-13
I have tried every option offered on this forum except the acpi=off feature and I am a bit nervous about trying this option. I am new to linux and I had the same problem with Saybayon so I decided to try this OS. I need basic simple command written out for me to get this fixed.

Thank U

Mel

---

### Post by burnttoast11 on 2007-10-14
Hey,
I also have a Toshiba laptop and had a problem with sound when I first installed ubuntu.  I have a different model, but here is what fixed mine.

```
sudo gedit /etc/modprobe.d/alsa-base
```
Then add this line to the bottom of the file.
```
options snd-hda-intel model=3stack
```
Restart computer and see if it worked.

P.S.- I am also a Linux newbie, so listen to me at your own risk.  :???:

---

