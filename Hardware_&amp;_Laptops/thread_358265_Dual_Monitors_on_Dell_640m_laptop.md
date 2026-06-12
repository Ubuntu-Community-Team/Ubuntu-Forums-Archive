---
title: "Dual Monitors on Dell 640m laptop"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by m_janos on 2007-02-10
After mucking around I finally got Dual screens working. The laptop monitor in working in 1440x900 mode and the external monitor E177FP is working in 1200x1024 with Xinerama. The external monitor is on the right of the laptop However while windows on the laptop will maximize properly on the external monitor I cannot move windows to the far right hand side of the screen. 
In addition when I maximize a window the window comes up partially on the laptop monitor and does not occupy the entire external screen. 

My Xorg setup is strange as well. I have the define the external LCD as the main screen and make the laptop monitor as being to the leftof the external LCD. X dies pretty much if I change anything to do with display in this file.

---

### Post by veloce on 2007-02-10
Just a me too post sorry.

Based on a another thread, I have improved things a little by using the line
virtual 1280 1024

in the display section of each monitor.  now the second screen works quite well and I just get the strange dragging and maximising behaviour on the main screen.

---

### Post by m_janos on 2007-02-12
I tried the Virtual keyword on both monitors but it didn't make any difference, the right hand screen (external LCD) still is quirky with regards to windows. I don't think it is a settings thing but a bug in the software

---

### Post by veloce on 2007-02-12
With more searching I found a solution to my problem of being unable to drag windows all the way to the right.  Looks like gnome remembers some stuff that you don't want it to.  The answer - repeated on another Xinerama thread:

Delete the ~/.gconf/desktop/gnome/screen folder.

My desktop now extends all the way across.

---

### Post by m_janos on 2007-02-12
You are a genius! It works.

Michael

---

