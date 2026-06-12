---
title: "Keyboard wont focus after resume from suspend/hibernate"
date: 2009-12-26
forum: Hardware
---

### Post by demersus on 2009-12-26
Hey, I know this has been asked before, but I cannot seem to find a suitable resolution for my particular problem.

Whenever my laptop recovers from hibernation or suspend, it will come to a screen  to unlock the session.  At this point, the mouse (touchpad) works fine, however the laptop's keyboard will not work.  

I think this is an xorg or kdm issue because i am able to select 'start a new session' and it will take me to the kdm login screen in which my keyboard will work fine.  But if I try to switch back to my existing session, the keyboard still refuses to work!

This is what I am running:
Gateway Laptop NV5302u
Kubuntu 9.10 AMD64
fglrx ati driver (from ubuntu repositories)

---

### Post by demersus on 2009-12-29
The only way I was able to get this to start working correctly is to Dump all of my Kubuntu stuff and install ubuntu-desktop. I switched to Gnome.

After switching my system from Kubuntu to Ubuntu, I had problems with suspend/hibernation as well, but it was a different problem.  This time it would not suspend, or hibernate at all. It would simply lock the screen. 

If you are experiencing the above problem, make sure that 'pulseaudio-utils' is installed. After searching the internet for hours, I found this little tidbit.    All my suspend/hibernate errors are fixed (in Gnome and GDM).  Who knows about KDE4 and KDM?

I really wish KDE4 and Kubuntu worked as well as Gnome. :(  I miss my KDE.  What happened to you?:confused:  Grrrrrr.....

So for now, this is solved by using the default Ubuntu(Gnome) installation.

---

