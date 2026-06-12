---
title: "some questions about VNC."
date: 2008-11-10
forum: General Help
---

### Post by pedrotuga on 2008-11-10
Ok, my parents have now ubuntu on their computers and they are very happy with it. Problem is, I live in another country and I can't visit them so often, so whenever they have a problem, they have to wait forever for me to get there and fix it.

SSH would be enough, except that sometimes it would be really handy to check visually what their talking about.
Also, I don't know if this is possible, if I connect to their desktop usng VNC, can they see the mouse pointer moving? That would be best.

I never used VNC, which packages do I need to install?
Does the default installation runs it as a gnome service? is it added to the boot somewhere? I would like it to be turned on manually whenever necessary for security resons.

---

### Post by rampageoberon on 2008-11-10
Ubuntu comes with Vino-Server built in which allows sharing of your desktop.

Go to System -> Preferences -> Remote Desktop.

It can be enabled by your parents whenever you need to so might be ideal. But you can also use tightvncserver aswell.

---

### Post by pedrotuga on 2008-11-21
Thank you. That was helpfull.
It works like a charm.

---

### Post by rampageoberon on 2008-11-22
Well done! Good to hear you've got it working.

Please do mark this thread as solved :)

---

### Post by KeyserSoze93 on 2008-11-22
Enable remote desktop, like rampageoberon said, and then install xtightvncviewer on your PC and use like so "xtighvncviewer -via you@parents localhost" where you@parents is what you would log in as with ssh.

This tunnels the VNC over ssh.

---

### Post by pedrotuga on 2008-11-22
I like vinagre quite a lot as it is simples an funcional.

ssl is not a requirement at them moment as this is just for occasional problem solving.
But since you came up with that I take the chance to ask this:

That would be the same as creating a tunnel using ssh and ten normally connect to that tunnel using any client, right?

---

### Post by tealio on 2008-11-22
If you're going to be using VNC over the internet, it's a good idea to tunnel the connection through SSH, so that it's encrypted... there's a very simple to follow guide [here.]("http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html") if you need more, just google *vnc ssh tunnel linux*.

---

