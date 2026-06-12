---
title: "vnc access before local login"
date: 2008-11-04
forum: General Help
---

### Post by ufis on 2008-11-04
I have an ubuntu 8.04 box with vino installed as vnc server.

Everything works fine as I want it to except for one thing.

I have to log in locally to the ubuntu box before it will allow any vnc connections.

Is there a way to set it up that will allow vnc connections to the ubuntu box right after a fresh restart and without the need to log into the box locally?

---

### Post by Peter09 on 2008-11-04
Hi,
you can do - but I have always found it a problem because you need to configure a VNC server. Perhaps someone else can help you there.

I have found the best way is to install openssh-server on your 'server'. This alows you to login through ssh. If you need a proper desktop install nxFree on top of that. Its relatively painless. Openssh-server is in the repositories.

---

### Post by ufis on 2008-11-04
Thank you for the freenx suggestion. If I do not come right with vnc I will try that out.

My vnc server is already installed, and working. As is ssh.

My proplem is that I can only connect via vnc once someone has logged on to the server locally.

So my first solution is to try and get the vnc server to start up with the os, and not only once a user logs in.

---

### Post by Peter09 on 2008-11-04
Yes,
thats always been my problem. VNC is really designed to share desktops. Before you login you have no desktop running. There are ways of doing it but is not easy as it requires fiddling with the window manager as well.

---

### Post by TyTiger on 2008-11-04
> **ufis said:**
> Thank you for the freenx suggestion. If I do not come right with vnc I will try that out.

My vnc server is already installed, and working. As is ssh.

My proplem is that I can only connect via vnc once someone has logged on to the server locally.

So my first solution is to try and get the vnc server to start up with the os, and not only once a user logs in.

One option is to have the system log in automatically. (local) at least then when you restart it, Gnome/KDE/Xfce will log in by its self and you will then have access to the desktop :)

though this is kinda insecure if you dont set a password for VNC.

---

### Post by ufis on 2008-11-05
> **TyTiger said:**
> One option is to have the system log in automatically. (local)

Thank you. I was not aware of this feature. Now it would be ideal to have it lock the screen right after login.

And yes, my vnc has a password :)

---

