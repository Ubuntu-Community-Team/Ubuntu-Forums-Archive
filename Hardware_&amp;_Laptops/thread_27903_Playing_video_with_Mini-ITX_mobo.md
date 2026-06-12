---
title: "Playing video with Mini-ITX mobo"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by PentiumSlayer on 2005-04-18
I'm using 5.04 on Via EPSD mini-itx board with Samuel CPU 800 MHz. I couldn't get video to display properly. Previously it didn't work in 4.10 either. I used VLC for GTK, VLC for Gnome, Totem and Mplayer. None worked. Any ideas?

---

### Post by TravisNewman on 2005-04-18
[QUOTE=PentiumSlayer]I'm using 5.04 on Via EPSD mini-itx board with Samuel CPU 800 MHz. I couldn't get video to display properly. Previously it didn't work in 4.10 either. I used VLC for GTK, VLC for Gnome, Totem and Mplayer. None worked. Any ideas?[/QUOTE]
 Define "couldn't get video to display properly"

Do you mean it didn't show at all, it was garbled, it skipped? If either, explain how it was garbled, etc.

---

### Post by PentiumSlayer on 2005-04-18
OK silly me forgot to elaborate.

I got garbled video, but sound is OK.

When I used 4.10, I *could* get video if opened 2 instances of VLC. The first one would be labeled "Xvideo" and was garbled. The second window was labeled "X11" and was OK even if very slow. I thought upgrading to 5.04 would solve the problems but now couldn't even get the slow video.

---

### Post by Christopher Williams on 2008-02-06
I had a similar problem with WMV's

In VLC try:
  Edit Preferences
  Expand Video
  Select Output Modules
  Tick the Advanced Options box in bottom right of dialog
  Then choose X11 Video Output from the auto-magically appearing combo-box.

Hope that helps someone :o)

---

