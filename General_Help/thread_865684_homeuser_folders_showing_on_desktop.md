---
title: "/home/user/ folders showing on desktop"
date: 2008-07-20
forum: General Help
---

### Post by koga on 2008-07-20
Hi, for some unknown reason my /home/user files have appeared on my ubuntu desktop. The files still show in the /home/user directory but when i try to delete them from the desktop it also removes the files from my home directory. Has this happened to anyone else before?
I tried using the "rm -rf .gnome .gnome2 .gconf .gconfd .metacity" command from the terminal to reset the desktop but that did not solve the problem. 
I don't think i did anything strange to cause this, i did delete my old distro-versions from synaptic yesterday so they dont show in the grub boot menu, could that have caused this?
Any help appreciated, thanks.

---

### Post by jonian_g on 2008-07-20
I dont think so, because I have deleted mine too but nothing like that happened.

---

### Post by jonian_g on 2008-07-20
I found something that might solve you problem. You might have set the home dir to be used as your desktop.

Open a terminal and type:

```
gconf-editor
```

On the window that comes up go to

apps>nautilus>preferences and look on the right side of the window for the value "desktop_is_home_dir". If it is checked, uncheck it, logout and the icons will disappear.

---

### Post by koga on 2008-07-21
No luck there, the box is unchecked. Thanks though.
Im not sure if this has anything to do with it but my /home/user folder now has a tiny little desktop icon to the top right of it as well as a house symbol which wasn't there before.

---

### Post by koga on 2008-07-21
Solved the problem.

I ran 
gedit ~/.config/user-dirs.dirs and then deleted these two lines:

XDG_DESKTOP_DIR="$HOME"
XDG_DOWNLOAD_DIR="$HOME"

and then ran
xdg-user-dirs-update

Logged out and the problem was fixed. 

Cheers,

---

### Post by CatKiller on 2008-07-21
Don't forget to mark the thread as solved.

---

### Post by koga on 2008-07-21
Sorry, how do i do that?

---

### Post by CatKiller on 2008-07-21
Thread Tools, at the top of the page.

---

### Post by TACITVS on 2011-08-24
You can also uncheck show_desktop in gconf-editor>>app>>nautilis>>preferences. That worked for me

---

