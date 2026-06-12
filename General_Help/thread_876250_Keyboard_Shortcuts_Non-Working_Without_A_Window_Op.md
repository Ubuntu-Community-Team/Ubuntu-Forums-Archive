---
title: "Keyboard Shortcuts Non-Working Without A Window Open"
date: 2008-07-31
forum: General Help
---

### Post by cegpope on 2008-07-31
On two different computers one Gutsy one Hardy, both using Metacity in Gnome (no compiz), keyboard shortcuts will not function without an open window on screen. 

Keyboard shortcuts do nothing without something open on screen; minimized programs or programs open on other workspaces do not count.

---

### Post by cegpope on 2008-08-04
Thoughts?

---

### Post by cegpope on 2008-08-28
having this problem on a third computers now. Setup another computer with Ubuntu without compiz running and keyboard shortcuts will not work on this one either, unless a program is open and visible on screen.

---

### Post by cegpope on 2008-08-29
I just had a break through.

Keyboard shortcuts work fine with conky disabled, but if conky is running on the desktop, then a program that runs in a window must be open for keyboard shortcuts to work.

Now I just have to figure out how to have conky on and keep shortcuts working.

---

### Post by cegpope on 2008-08-29
I just played with my .conkyrc a bit, and have discovered that by completely removing > # Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

despite the config saying own_window is need with nautilus, conky is running integrated with the desktop and keyboard shortcuts are working perfectly, I have no idea what one thing has to do with the other, but it works now. (at least on this computer, it will be a few days until I can check the other two)

---

