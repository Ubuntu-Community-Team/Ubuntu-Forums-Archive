---
title: "computer won't load from a live cd"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by fragility14 on 2008-01-19
Hi, I messed up my install of Kubuntu by messing around with KDE4, and in the process of trying to remove it I am unable to load my xserver, I am trying to reinstall from a livecd, and a livecd which I have tested on another computer will not load, my computer automatically loads from the hard drive, regardless of the order in the BIOS, and is unable to load from a CD even with the hard drive plugged in, it will say "Error, Insert System Disk and hit Enter"

I am currently trying to fix the actual install...(incidentally, what is the command to run the xserver if it is automatically going to the text based install?) but in the mean time, would very much like suggestions for making it read off of a life cd...never been a problem before.

thank you

---

### Post by alan34 on 2008-01-20
To re-instate xserver in a terminal/text boot.

sudo dpkg-reconfigure -phigh xserver-xorg

This command is in your xorg.conf file. To check do a 

 less /etc/X11/xorg.conf

type "q" to exit no quotes.

Some computers will bring up a boot menu if you hit one of the function keys when the computer
is first switched on, on my dell it is F12 you could try playing with them.

Good function key hunting

---

