---
title: "laptop as monitor"
date: 2009-04-18
forum: Hardware
---

### Post by Ampi on 2009-04-18
I have an old laptop that has no harddisk and no battery (I only have an adapter). 
Is it possible to connect it to my (desktop) computer to use as it solely as a monitor? 

When I connect the laptop as it were my monitor it only shows the celeron logo and then it stays black. 
Is it possible at all or am I doing something wrong?

---

### Post by scgroup on 2009-04-18
You cannot use your laptop as a monitor via its VGA connector.  The VGA interface is not symmetrical.  A computer can only send video; a monitor can only receive it.  The VGA connector on your laptop is intended for connection to an external monitor and is send only.

If your laptop has a CD-ROM or a suitable USB flash drive, you should be able to boot Ubuntu or other OS.  Then, via a network connection to your desktop machine, you could display the desktop's applications.  The simplest way (but lower in performance) is to use VNC or a similar remote access program.  Alternatively, you could tell your desktop apps to display on the laptop's X server.

---

