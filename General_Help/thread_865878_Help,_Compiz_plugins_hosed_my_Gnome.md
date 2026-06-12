---
title: "Help, Compiz plugins hosed my Gnome"
date: 2008-07-21
forum: General Help
---

### Post by Foxblood on 2008-07-21
Hi, 
I installed some updates for Compiz in order to achieve the globe effect. Bad mistake. After I restarted I have nothing but a black screen. The mouse moves. What I'd like to do is undo what it was that I did. Can this be done? Can Compiz be prevented from starting? I used Synaptic to install these plugins, is there a way to "undo" the installation from there? I'm using Gnome but I also have Xfce, which sort of works - flickering screen, flickering Conky and unresponsive Awn. I'm not sure what will and won't work, though.
Anyone have any suggestions?

---

### Post by stldirty on 2008-07-21
can u uninstall the plugins from xfce?  are you familiar with installing and uninstalling via the terminal?

if it really is just the plugins messing up ur computer then a sudo apt-get remove <plugin> should suffice.  if they messed with the xorg then ur gonna have to rebuild it...see if u can uninstall the plugins first.  u might have to do it from the recovery menu.

---

### Post by Foxblood on 2008-07-21
Thanks for the quick response. I used Xfce to disable Compiz and now I have a more-or-less usable desktop. Is there any way to identify exactly what plugins it is that I installed? Would complete removal and re-install of Compiz be a better idea?

---

### Post by Foxblood on 2008-07-21
I see where I made my mistake. When I was installing the plugins I inadvertantly added a Hardy Heron repo and I'm using Gutsy. I still don't know how to fix it. 
This is what I added to my software sources: [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu). It's Hardy Main.

Any ideas?

---

