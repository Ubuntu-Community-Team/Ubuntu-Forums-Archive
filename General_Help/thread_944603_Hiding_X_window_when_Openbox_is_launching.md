---
title: "Hiding X window when Openbox is launching"
date: 2008-10-11
forum: General Help
---

### Post by shawnrgr on 2008-10-11
I loaded up only the base install of ubuntu, then threw on xorg, openbox and nvidia-glx. All works great except for when Openbox is loading I see the x-server window (black and white with 'x' for mouse) flash on the the screen before openbox takes over. I want to hide this. I've never seen this in the default install of ubuntu or xubuntu so I know its possible.

If it matters...I don't have a login manager running. I have the system setup to auto login with rungetty then my .bashrc runs startx.

---

### Post by cariboo on 2008-10-11
You may want to install xdm to get rid of the initial screen, but that sort of defeats the purpose of using Openbox.

Jim

---

### Post by shawnrgr on 2008-10-11
Yea, this is for my media center pc, running Boxee media center. The goal is speed. The faster I can boot up and be in Boxee the better. That why I didn't install a login manager. I want to go straight through and not have to load the login manager at all. saving time and mem

---

### Post by urukrama on 2008-10-11
I'm not sure you can do anything about it. One of my computers doesn't use a session manager/login screen either, and I've added *xsetroot -solid black &* to my .xinitrc. The black and white X screen won't go away, but it appears very briefly before it is turned solid black.

If there is a solution to get rid of it completely, I too would like to know.

---

### Post by shawnrgr on 2008-10-11
If any login manager can hide it, there must be a way to do it without one. Anyone?

---

