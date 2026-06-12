---
title: "compiz running slow"
date: 2008-07-21
forum: General Help
---

### Post by michaelbmcgee on 2008-07-21
hello,
i am having a problem getting compiz running normal. i used envy to install the ati driver and it installed successfully and i enabled desktop effects and they work, just slow. i then uninstalled the driver and compiz and downloaded the driver from the ati website and installed it myself but had the same problem. oh i have a express x1200 card in my laptop.

i tired another distro call sabayon and compiz ran fast, even off the live cd. any suggestions on how to get compiz working fast in ubuntu?
thanks

---

### Post by chavanak on 2008-07-22
Am not very sure but ati has always been a problem :( Maybe you can try disabling some plugins. The reflection plugin and a few others might help

---

### Post by michaelbmcgee on 2008-07-22
i tired that but compiz still ran at the same speed. the thing that gets me is that i can turn on all the settings for compiz in sabayon linux and it still runs at full speed. i do not care for sabayon and still want to use ubuntu.

does anybody know if i need to unistall something to make it run faster. i was told xgl but wasnt sure if that was true or not. when i get back from class im gonna unistall compiz and reinstall it and see if that happens to do anything when i get back from class. anybody have any ideas?

---

### Post by erkanea on 2008-07-22
pasting the result of these commands may take attention on whats going wrong

fgl_glxgear
glxinfo
glxgears
fglrxinfo

and ofcourse your /etc/X11/xorg.conf

edit : you may find it usefull to check [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by michaelbmcgee on 2008-07-22
ok i got it working right. what i did was reinstall hardy and do all the updates and uninstall all compiz and components, then install the latest catalyst driver (8.6) reinstall compiz and its running good now. the only problem i have is the borders of the window "stick" to the panels and such when im moving the windows around. how do i disable this?
thanks

edit: ok one more question, when i drag windows and move them around they flicker a little bit. any ideas to what this may be?

---

### Post by chaospike on 2008-07-28
for future reference, xgl does make an ATI Radeon x1300, at least using Hardy/CompizFusion/fglrx, very very slow. I've gotten Compiz running with Big Desktop via fglrxcontrol/amdcccle but it won't stick. The login manager prior to loading Gnome does a dual desktop, non-cloned but once Gnome w/ Compiz-Fusion load after login it returns to Cloned display, I'd believe checking out the gdm conf would be the next step but I'm going with the same steps as you and reinstalling to start fresh. I remember on a previous card having two cubes that rotated next to each other, but allowed windows to go between displays, not positive if that was a nvidia or ati though.

---

