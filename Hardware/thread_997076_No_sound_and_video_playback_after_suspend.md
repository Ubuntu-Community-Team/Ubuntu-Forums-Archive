---
title: "No sound and video playback after suspend"
date: 2008-11-29
forum: Hardware
---

### Post by MixedMadness on 2008-11-29
I'm running Ubuntu 8.10 on a Lenovo y510.  When the computer suspends, then recovers, all video and audio playback quits working.  I can't playback sound or video files at all, and the sound quits regardless of all levels set to max.  It only happens when the computer suspends, a restart is required to get it back.  Weird.  Has anyone had anything similar happen?

---

### Post by Vaidok on 2008-11-29
I had the same problem a week ago.  I had to reinstall my restricted ATI driver, redo xorg.conf file, and tell my video card acpi services off.
What video card do you have?

---

### Post by MixedMadness on 2008-11-29
I've got the Nvidia GeForce 8600M GT.

---

### Post by Vaidok on 2008-11-29
Try finding some way to turn the acpi services off for the card.  They are what tell your computer how to sleep.  Or you could play around with the options in "/etc/default/acpi-support".

---

