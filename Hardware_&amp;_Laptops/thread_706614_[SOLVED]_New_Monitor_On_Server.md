---
title: "[SOLVED] New Monitor On Server"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by dethredic on 2008-02-24
Ok, I got a new monitor for my server, but look at this:
> 
root@server1:/home/phil# sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080224161056
root@server1:/home/phil# 


How can I reconfigure my monitor, cause I am stuck with non widescreen resolutions.

---

### Post by jpeddicord on 2008-02-24
Unless you are using Hardy (you shouldn't be on a server!) you can probably reconfigure your display just by running **sudo dpkg-reconfigure xserver-xorg** without the -phigh option.

You can also edit /etc/X11/xorg.conf, but that can be a pain. :)

---

### Post by dethredic on 2008-02-24
sorry I am new to the server buisness, what is hardy?

edit: without the phigh it worked

---

### Post by jpeddicord on 2008-02-24
Hardy is the code-name for the current development version of Ubuntu, to be 8.04. I mentioned it because it uses a newer version of X that doesn't work the same way, so configuring it would work differently.

---

### Post by dethredic on 2008-02-24
Alright, thanks for your help man.

---

