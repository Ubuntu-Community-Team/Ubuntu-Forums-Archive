---
title: "Videos in the windows switcher"
date: 2008-09-11
forum: General Help
---

### Post by Nathan_M on 2008-09-11
Hi, if I have a video playing in MPlayer/VLC/etc, and I switch windows by pressing the "super" (Windows) button and tab, the video doesn't move with the window. Is there some setting in Compiz to do this? I know it's technically possible, because it used to work under Windows Vista.
Thanks,
Nathan

---

### Post by sayakb on 2008-09-11
Compiz does not integrate well with OpenGL video output mode.
To fix this with VLC, launch VLC, goto Settings->Preferences
Check the *Advanced options* checkbox (bottom right)
On left panel, expand Video->Output Modules and set the Video output module to **X11 video output**.
Save the settings and restart VLC.

---

### Post by detroit/zero on 2008-10-10
Works like a charm. I've been wondering about that for a while now. Thanks!

---

