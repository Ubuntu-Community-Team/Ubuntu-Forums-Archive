---
title: "Slow video no sound after laptop left on a while"
date: 2008-10-16
forum: Hardware
---

### Post by LieToPurify3 on 2008-10-16
After my laptop has been on for a while, sometimes when I try to play video, it will play with no sound, or at like 1 fps with no sound too.  Any idea what could be causing this?  A restart always fixes the problem temporarily, and this doesn't happen all the time. It seems to happen after my laptop has been on after a while, and I haven't noticed it immediately after boot up.  This could just be a coincidence though.  Any help would be appreciated. 

Ubuntu 8.04
Toshiba Satellite A105-S1712

---

### Post by LieToPurify3 on 2008-10-17
please?

---

### Post by x20mar on 2008-10-18
I'm getting this problem as well, thou I found that the video problem doesn't occur in vlc but it does in mplayer.

Laptop: Toshiba A200-1AI

Possible reasons why:

New ubuntu Kernel (I would test the old one but I uninstalled it and I can't remember what version it was),

Installed Ubuntu-laptop package.

---

### Post by x20mar on 2008-10-18
Solved:

Fix it by going to

System > Preferences > Sound

and change all the playback options from Autodetect to ALSA and everything seems should be working now.

---

### Post by x20mar on 2008-12-07
secondary solution: uninstall adobe air

---

