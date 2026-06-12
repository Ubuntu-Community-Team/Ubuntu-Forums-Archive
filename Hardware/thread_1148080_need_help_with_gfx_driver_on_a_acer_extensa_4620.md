---
title: "need help with gfx driver on a acer extensa 4620"
date: 2009-05-04
forum: Hardware
---

### Post by devroute on 2009-05-04
okay I have just installed ubuntu 9.04 a few days ago i have a acer extensa 4620 laptop and for some reason i can't enable desktop effect's i've googled for hours and can't come up with anything tried everything i can think of can someone please help me :<

---

### Post by mikedep333 on 2009-05-04
It sounds like you have the Intel GMA 3100 graphics adapter.

That should "just work" with the desktop effects.

You are trying to enable it from the appearance settings, right?

---

### Post by devroute on 2009-05-04
> **mikedep333 said:**
> It sounds like you have the Intel GMA 3100 graphics adapter.

That should "just work" with the desktop effects.

You are trying to enable it from the appearance settings, right?


yes and no luck i've even tried to install other nvidia drivers threw add / remove and no luck w/ that either it doesn't even show up in hardware only thing that shows up in hardware is wireless card :/

---

### Post by devroute on 2009-05-04
also here's something that might help =p this is the graphics card i have

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

---

### Post by devroute on 2009-05-04
still need help :/

---

### Post by mikedep333 on 2009-05-04
First of all, the nvidia driver is only for nvidia hardware. Ubuntu automatically loads the intel driver automatically for your intel adapter.

Let's try reconfiguring the X server.

Run:
```
sudo dpkg-reconfigure xserver-xorg
```
And then restart your computer.

Then see if you can enable the effects through appearance settings.

If not, post the contents of your /var/log/Xorg.0.log

---

### Post by devroute on 2009-05-04
> **mikedep333 said:**
> First of all, the nvidia driver is only for nvidia hardware. Ubuntu automatically loads the intel driver automatically for your intel adapter.

Let's try reconfiguring the X server.

Run:
```
sudo dpkg-reconfigure xserver-xorg
```And then restart your computer.

Then see if you can enable the effects through appearance settings.

If not, post the contents of your /var/log/Xorg.0.log


thanks it worked was playing around in class today w/ the boxes haha =p

---

