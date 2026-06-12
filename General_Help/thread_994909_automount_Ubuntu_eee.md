---
title: "automount Ubuntu eee"
date: 2008-11-27
forum: General Help
---

### Post by helbent forleder on 2008-11-27
I am confused.
I have recently started using Ubuntu eee on my Asus eee 1000H, and for the most part I have to say that it's excellent.
Despite my joy, there's is one sticky matter, that I wouuld love to resolve once and for all! That is that it refuses to automount thumbdrives and SD cards.
If I plug in a thumbdrive the system will tell me that it can't mount it because I have to be SUDO or root or whatever it's called. So, I open gnome-terminal and type:```
sudo mount /dev/sdb1 /media/thumbdrive
```
This mounts the device and it is readable, but it's not writable...:(
So in frustration (keep in mind that I know very little about Linux) I tried this command:```
sudo mount -o owner /dev/sdb1 /media/thumbdrive
```
It had no special effect though.
What makes it writable is to unplug (I never 'unmount') the drive and replug it. Then it pops open Nautilus and I can read and write to my poor hearts content. :):confused::lolflag:
What's the deal?
Can someone guide me in making my eee simply automatically mount media that I plug in? I'd like to skip the 2 minute process of making my mounts accessible.
THANKS IN ADVANCE!

---

### Post by helbent forleder on 2008-11-28
Help?:confused:

---

