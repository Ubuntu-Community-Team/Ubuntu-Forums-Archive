---
title: "[SOLVED] How to send a Ctrl-Alt-keystroke to a Vncviewer Applet in Ubuntu"
date: 2008-08-12
forum: General Help
---

### Post by prankst3r on 2008-08-12
Does anyone know how a Ctrl-Alt-<keystroke> can be sent to a vncviewer applet? Currently if I try to Ctrl-Alt-F1 to a terminal, my system interprets the keystroke and dumps me into a terminal on my end. Any suggestions?

---

### Post by firefeather on 2008-08-12
You can use F8, I believe, to get a VNCViewer menu; I don't have a useable VNC connection right now to test it on, but I vaguely remember it allowing you to send certain system keystrokes.

---

### Post by prankst3r on 2008-08-12
> **firefeather said:**
> You can use F8, I believe, to get a VNCViewer menu; I don't have a useable VNC connection right now to test it on, but I vaguely remember it allowing you to send certain system keystrokes.

Unfortunately F8 doesn't work with the applet - it does work with the standalone vnc client, but i am constrained to the applet version unfortunately...

---

### Post by prankst3r on 2008-08-13
The irony is that what I am doing is taking a Redhat Virtual training course (part of the RHCE track) and because they are embedding the vncviewer applet it practically necessitates that we use a non-linux OS (read windows) as any linux OS is going to intercept a Ctrl-Alt-F[1-7] instead of passing it through to the vncviewer applet.

---

### Post by prankst3r on 2008-08-13
I got an answer that works for changing terminal. Just execute ```
chvt 1
``` where the 1 option indicates the terminal to switch to. This requires the root user if you're running it on a non-ubuntu distro otherwise just sudo it.

---

### Post by firefeather on 2008-08-13
So is that a mark-as-solved solution? :) Good save!

---

