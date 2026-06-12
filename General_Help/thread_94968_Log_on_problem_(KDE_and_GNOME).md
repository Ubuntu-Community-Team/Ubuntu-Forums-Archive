---
title: "Log on problem (KDE and GNOME)"
date: 2005-11-25
forum: General Help
---

### Post by irv on 2005-11-25
I had to reboot my PC and when it comes up I get the login screen. It does not make any difference if I login to KDE or GNOME desktop, it keeps coming back to the logon screen. I can get into the failsafe mode only.

Any suggestion on what to do? I had to logon to my laptop just to get to this forum.
Thank for the help anyone.

---

### Post by irv on 2005-11-25
Problem solved, I didn't have right to my home folder.

sudo chown -R username /home/username 

This fixed the problem.

---

### Post by irv on 2005-11-25
I found another little tid-bit about SSH. I have installed Konqueror, and if I use the remote from the Network place, I can ssh to the server from my workstation. The problem seems to be in GNOME desktop on Ubuntu 5.10 Breezy. It has to be a bug. 
I would like to report this, does anyone know where to do this?

sorry I put this is the wrong thread.

---

