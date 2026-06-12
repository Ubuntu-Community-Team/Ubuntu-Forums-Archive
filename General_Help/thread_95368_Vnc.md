---
title: "Vnc"
date: 2005-11-26
forum: General Help
---

### Post by termite on 2005-11-26
I am running an ubuntu machine and a winXP machine on my home network.  I want to use VNC to control my winXP machine from my ubuntu machine.  I can connect fine and speed isn't an issue.  However, while the keyboard works fine, mouse events don't seem to go through.  ie when I click on something in vncviewer, nothing happens on the remote machine.

Ideas?

---

### Post by jonatan on 2005-11-26
What VNC server on XP do you use?

---

### Post by termite on 2005-11-26
RealVNC 4.1.1 free edition.

---

### Post by jonatan on 2005-11-26
Never tried RealVNC, but I have TightVNC working flawlessly on many XP-installations. The development version is fast and I've had no stability problems with it.

---

### Post by termite on 2005-11-26
thanks.   I'll try it when I get back home.

---

### Post by 0okami on 2005-11-26
[QUOTE=termite]I am running an ubuntu machine and a winXP machine on my home network.  I want to use VNC to control my winXP machine from my ubuntu machine.  I can connect fine and speed isn't an issue.  However, while the keyboard works fine, mouse events don't seem to go through.  ie when I click on something in vncviewer, nothing happens on the remote machine.

Ideas?[/QUOTE]

on your XP machine, RT.Click on the icon in the program RealVNC tray (next to the clock) select properties tab and go to the tab that says "Input." 

Is "accept pointer events form clients" enabled? If not, enable it. That should do the trick. Also, put a check on everything in the Input tab (read it first to see if it matches what you want VNC server to do) 

thats all. Reply if this helped you so we know its solved.

---

