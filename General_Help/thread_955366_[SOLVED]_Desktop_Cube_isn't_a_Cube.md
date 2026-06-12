---
title: "[SOLVED] Desktop Cube isn't a Cube"
date: 2008-10-22
forum: General Help
---

### Post by wardrich on 2008-10-22
I'm using Compiz on Ubuntu 7.1, and for some reason my desktop cube isn't a cube.  If I hit ctrl-alt and drag the mouse left/right it only flips between 2 desktops, and they're paper thin.  I have 4 desktops set in gnome.  There's no options in either the desktop cube or the rotate cube that let you pick how many desktops you want... am I missing something?

---

### Post by dark_harmonics on 2008-10-22
You need to set the number of horizontal desktops in the compiz config manager (sometimes listed under system -> Preferences -> Advanced Desktop Settings). 

Go into the General options and then the desktop size tab. Set it to the desired number of desktops. 

If you do not have the advanced desktop settings or compiz config manager options, then you need to install compizconfig-settings-manager with

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by wardrich on 2008-10-22
> **dark_harmonics said:**
> You need to set the number of horizontal desktops in the compiz config manager (sometimes listed under system -> Preferences -> Advanced Desktop Settings). 

Go into the General options and then the desktop size tab. Set it to the desired number of desktops. 

If you do not have the advanced desktop settings or compiz config manager options, then you need to install compizconfig-settings-manager with

```
sudo apt-get install compizconfig-settings-manager
```

Oh, thanks. I actually already had that package on, I just had it set to 2vert and 2horiz.  I thought the cube would just adjust accordingly.  Thanks :D

---

### Post by jjmono987 on 2008-10-22
yea if u have 5 desktops it wont have a cube. So right click on the workspaces and hit preferences then put it to 4 and you will have the cube. and if u have compix u can make alot of effects to the cube.

---

### Post by cl0ckwork on 2008-10-22
please mark thread as solved

thanks you!

---

