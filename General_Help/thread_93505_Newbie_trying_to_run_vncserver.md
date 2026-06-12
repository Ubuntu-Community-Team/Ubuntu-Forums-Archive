---
title: "Newbie trying to run vncserver"
date: 2005-11-22
forum: General Help
---

### Post by pbb on 2005-11-22
I was trying to enable friends to connect to me through VNC, so they can help me configure my computer.

Not a total newbie anymore, I first open Synaptic to see if Ubuntu already comes with VNC. Doing a search, I find vnc-common is even already installed.
Opening the package properties to see where it is installed, finding the documentation in /usr/share/doc/vnc-common. Reading this, I learn all I need to do is entering the "vncserver" command in the terminal.

Doing so however, just results in "bash: vncserver: command not found"... Okay, doing a search of my whole system for vncserver. Nothing is returned!

Re-installing the package through Synaptic changes nothing.

Is the vnc-common supplied with Ubuntu not complete? Does it only contain the viewer? But, then why does it contain vncpasswd which would be useless without vncserver? The documentation mentions nothing, just talks about using vncserver...

Anyone who can tell me more? Thanks, Peter

---

### Post by soulestream on 2005-11-22
gnome comes with a vncserver.

desktop -> preferences -> remote desktop 

just turn it on and set password


soule

---

### Post by pbb on 2005-11-22
Yeah, I found that one also afterwards. Still puzzles me thought, that the "vnc-common" talks about some command "vncserver" but I am not able to find it.
Does anybody know if it is true that only a partial vnc-common is included with Ubuntu?

---

