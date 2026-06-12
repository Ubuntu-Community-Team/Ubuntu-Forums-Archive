---
title: "All look strange after recompiling the kernel"
date: 2005-01-29
forum: Installation &amp; Upgrades
---

### Post by edemark on 2005-01-29
Hi to all

I have a small problem. How to find out what went wrong witrh my kernel recompile? So the simptoms are the following everithing look strange from the boot up process onward. When gdm load it looks, I really do not know the right word in Inglish, something like vibrant and fleshy. (When i boot my old kernel X looks nice and sharp).
Same when I get into my account splash screen appears twice the second offsetted over the first. Inside gnome menus are dobbled buttons are dobbled so i just can not use it.

Any idea where to start to look for setting up my kernel correctly?
what i did was the following 
download source and tree of the kernel 
patch the kernel ([www.bootsplash.de](www.bootsplash.de)) 
make oldconfig (cp first .config file from /boot to /usr/src/linux)
make xconfig (setting up kernel following the Debian Graphical Bootsplash HowTo)
fakeroot make-kpkg clean
fakeroot make-kpkg --appent-to-version=.280105 kernel-image --initrd binary
installed those 4 pkgs that were the fruits of 6 hours waiting
then reboot


thanks in advance
edemark

---

### Post by piedamaro on 2005-01-29
Same deal here, I've got a FX5700 video card, I'm on hoary, I've built-in all the required drivers( vga etc. following the bootsplash howto for debian).
My situation is even worse, my screen is totally messed up, I can't even see what I'm typing.
The problem is the vga=791 parameter (tried othe resolutions to no avail), because if I remove the splash= parameter nothing changes. If I remove the vga= parameter too, the screen blanks totally (no mess but also no console, no X, while it's booting correctly!).
:(

---

### Post by edemark on 2005-01-29
Bad news 

I mean stil it was my first kernel compile, i have almost fallen a sleep waiting and no splash screen. i am actually trying to search for answers at bootsplash-discussion (sourceforge.net) if i find something i will let you know.


so any ideas?

---

