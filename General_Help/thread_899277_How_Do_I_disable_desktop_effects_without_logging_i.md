---
title: "How Do I disable desktop effects without logging in?"
date: 2008-08-24
forum: General Help
---

### Post by shafin on 2008-08-24
I'm having some problems with compiz which prevents me from logging in. So I somehow managed to reconfigure my xserver, I'm quite a noob, so it took me a lot of time and I didn't really realize how I did it. Then Desktop effects were turned off and all were running smoothly. Then I got adventurous again and tried to turn on desktop effects. Result? I'm back to the login screen, with the same old bug. Now I have IceWM and can log on to that. So is there any way I can change the desktop effects settings to no effects without logging in to gnome. I can edit the files on IceWM, so if editing a file can do it, I'm all for it.

Thanks in advance

---

### Post by Diabolis on 2008-08-24
Probably it will work if you modify configuration keys with **gconf-editor**. Just execute it from the terminal and a window, that looks like a Windows registry, will show up.

I don't know which is the exact value that you have to modify, but a good start is to give a look to this path: **/apps/compiz/general/allscreens/options/**

---

