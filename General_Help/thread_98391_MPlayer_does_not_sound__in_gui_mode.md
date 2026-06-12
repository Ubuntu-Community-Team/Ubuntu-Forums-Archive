---
title: "MPlayer does not sound  in gui mode"
date: 2005-12-03
forum: General Help
---

### Post by arkangel on 2005-12-03
I have install  MPlayer form source  ,all  ok  but using  gui mplayer it says error 

resqueted audio codec family not found  [mad]    (afm=libmad)  enable at compilation  but i can play everything  in non gui  mode 

any idea

---

### Post by sapo on 2005-12-03
Try opening the settings menu, and in the audio tab, changing the default audio driver to Alsa or another one.

When i compiled here.. it selected OSS by default, changing to alsa solved my problems.

---

