---
title: "Live CD problems. Laptop hardware issue?"
date: 2004-12-24
forum: General Help
---

### Post by qzio on 2004-12-24
Hi there.

I've tried the ubuntu live cd on my laptop. It usually runs debian. So I want to mount my reiserfs partion, but

# mount -t reiserfs /dev/hdXY /mnt/hda

gives me the special device dos not exist message. (I've tried different combinations of X and Y (It should be hda3 tough).

I've also tried to do this with knoopix with out success.

This is not a big issue, i only burned the cd to get a "feel" of ubunut and planing to install it on this laptop when i get the time.

But a bigger issue is that i can't start firefox/term/anything when I've configured my nic. This is really strange since the computer doesn't hang or anything like that, if i press the icon it just wont start, the computer thinks and all that but nothing happens.
This happens AFTER i've configured my NIC. If i start a Terminal before i configure the network it works and I can still use it and ping, ssh, etc. But I can't start a new one.
However i can click the "computer" or whatever it's called, and get a filebrowserwindow. 

Has anyone else seen this problem? am I the only one? is this a known bug? Can it be the "laptop-hardware-stupid-non-standard-shit-crap" issue?

---

### Post by mattsve on 2005-01-22
I have the same problem, after I have configured my wireless pcmcia card almost all applications fail to start since they suddenly can't connect to the xserver ("connection to ":0.0" refused by server" in the console)

Does anyone know if it's fixable?

---

### Post by Cloudchaser on 2005-01-29
I had the same problem, after configuring my wireless pcmcia card none of the apps would work.

---

### Post by DarthBart on 2005-02-03
I'm a newbie to Ubuntu/Linux/et al, but I am seeing the same problem on my desktop with Ubuntu Live CD.  After configuring Ethernet connection, apps won't start.

Anybody resolve this issue??  Could it just be a case of the Live CD, or would I see the same thing after installing the software directly?

---

### Post by C17H21NO4 on 2005-02-28
Just switch to another tty and reset your hostname.  The problem is that gnome doesn't like it when you change your hostname.

---

