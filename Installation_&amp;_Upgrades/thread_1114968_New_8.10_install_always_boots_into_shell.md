---
title: "New 8.10 install always boots into shell"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by Fil1976 on 2009-04-03
Hi there,

Apologies if I've missed a search result but I can't find anyone with the exact same problem that I have.

I have a Dell Mini and it came preinstalled with Ubunutu 8.04 - try as I might to upgrade I cannot do it so I took the task of installing 8.10 from scratch.

I ended up having to use the alternate install CD and everything went well until I tried to boot up for the first time.

I get the Ubuntu loading bar followed by a shell prompt:

Boor from (hd0,0) ext 3
Starting up ...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/sda5) = dev(8,5)
kinit: return to resume from /dev/sda5
kinit: No resume image, doing normal boot

Ubuntu 8.10 Kenana tty1

Kenana login: _

(Kenana is the name given to the laptop.)

I've trawled the web and found some hints but nothing worked.

According to sudo gdm start the Gnome Display Manager is running.
If I try sudo gdmsetup I get (gdmsetup:6049): Gtk-WARNING **: cannot open display.

Am I not doing something right?

Can anyone help? I think I may be forced back to 8.04 at this rate.

---

