---
title: "When does it stop being X and start being GNOME?"
date: 2008-09-11
forum: General Help
---

### Post by gamelord12 on 2008-09-11
I use the default Ubuntu 8.04 disc on my laptop, which of course comes with GNOME.  I've experimented with KDE, but only briefly, so I don't know if this issue happens in KDE as well.

I know that X is the window system that GNOME is based on, and I'm under the impression that KDE is based on it as well.  What exactly does X do that GNOME can't do on its own?  The reason I ask is that sometimes when I do things that need super user permission, the screen goes dark except for the password prompt box that comes on screen.  Sometimes when that goes away, most (but not all) of my panels on the top and bottom of the screen stay dark, while other parts light up the way they're supposed to.  The way this looks on-screen is just like in Windows XP when a window is drawn a million times on top of itself when you try to reposition the window, and that is an experience I don't want to have again.  Who is to blame here?  X or GNOME?  Is there a way to stop this?

---

### Post by Pro-reason on 2008-09-11
GNOME and KDE can't do *anything* on their own.

They both rely on X to create a graphical interface to work with.

X starts when the GDM log-in manager starts.  It stops when you log out of all graphical sessions.

At any time, hit Ctrl-Alt-Backspace.  That will shut down X.  You'll notice that GNOME and all graphical apps will be immediately killed.

---

### Post by gamelord12 on 2008-09-12
So which program is responsible for that glitch with the super user password prompt where parts of the panels stay dark until I mouse over them or click them.

---

### Post by Pro-reason on 2008-09-12
> **gamelord12 said:**
> So which program is responsible for that glitch with the super user password prompt where parts of the panels stay dark until I mouse over them or click them.
That could be X, part of GNOME, or some other graphical software, such as Compiz.

It could also be the case that all that software is doing things in the right way, but your video card clashes with them.

---

### Post by Anzan on 2008-09-12
In Linux the graphical environment is entirely separate from the kernel and even the GNU tools that emulate Unix. 

X makes a graphical environment possible.

GNOME and KDE and Xfce gather together many different elements to create a Desktop Environment that runs on X.

Window Managers like ion, awesome, ratpoison, Window Maker, Fluxbox, Openbox and so on allow the user to have a graphical environment but configure how different elements such as programs run or interact according to their own preferences.

---

