---
title: "How to set up remote desktop ubuntu to ubuntu"
date: 2008-11-12
forum: General Help
---

### Post by edrace562 on 2008-11-12
I am running ubuntu on both my laptop and desktop.  I would like to be able to access my desktop at home while at school on my laptop.  Anybody know where a good tutorial is that is meant for ubuntu to ubuntu computers?  All I can find is windows to Ubuntu.

Thanks!!!

---

### Post by Keen101 on 2008-11-12
[http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html)

There might be more and/or better ones, but that was the first one on a google search.

---

### Post by cariboo on 2008-11-12
There are several ways to do what you want. I wpuld help if we knew how you connect to the internet from your desktop.

If you just need to use the command line you can use ssh.If you want to do it graphically Ubuntu has remote desktop software installed by default.

Before I contiune let us know how your desktop is connected to the internet.

JIm

---

### Post by geirha on 2008-11-12
There are several ways.

1. VNC: Go to system -> preferences -> remote desktop and enable it. Choose at least one of the security options; using password would be the logical one in this case. On the laptop, you go to Applications -> Internet -> Remote Desktop Viewer and connect to your desktop computer's ip. If your desktop computer is behind a router, you may need to forward the vnc port (5900). Check [http://www.portforward.com](http://www.portforward.com) for instructions for your router.

This will only work if you are already logged in at your desktop computer.

2. SSH: Install [apt://openssh-server](apt://openssh-server) on your desktop, and on the laptop, run ```
ssh username@ip-adress
``` in a terminal to connect. As above, you'll need to forward the ssh port (22) if you're behind a router. ssh will only give you a shell on the other machine though, not the GUI, though you can start GUI applications with xforwarding. 

3. XDMCP: On the desktop, go to System -> Administration -> Login screen and enable remote login. On the laptop, install [apt://xnest](apt://xnest), then connect with Applications -> Internet -> Terminal Server Client. Choose XDMCP as protocol.

---

