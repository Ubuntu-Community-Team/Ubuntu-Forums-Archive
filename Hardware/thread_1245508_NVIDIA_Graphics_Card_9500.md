---
title: "NVIDIA Graphics Card 9500"
date: 2009-08-20
forum: Hardware
---

### Post by DevinMcElheran on 2009-08-20
I have a GeForce 9500, and I can't get the drivers installed, every time I try, it says I can't be running an x-server, but I don't know how to kill x. Any suggestions?

---

### Post by Lusse on 2009-08-20
CTRL + ALT + F5 will drop you to a shell. Log in and type:

sudo /etc/init.d/gdm stop

You should be able to install now.

Hoped it helped :)

EDIT: Remember that your running programs probably will quit ungracefully, it might be a good idea to log out first.

---

### Post by DevinMcElheran on 2009-09-03
Do you know of a way to do this offline, because I need to download some dependencies or something, or compile them myself, but I don't know where to get the necessary packages, and so on. I don't have an internet connection, and my wireless card isn't working under ubuntu. So I was wondering if there was a way to do this offline.

---

