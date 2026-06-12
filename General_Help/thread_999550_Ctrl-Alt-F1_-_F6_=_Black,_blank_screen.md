---
title: "Ctrl-Alt-F1 - F6 = Black, blank screen"
date: 2008-12-02
forum: General Help
---

### Post by tmastran on 2008-12-02
Ubuntu 8.10 / Nvidia driver

While in Gnome, Ctrl-Alt-F1 to F6 used to display a text console or tty. All I get now is a gray screen with no login prompt. If I login in blind and issue a command like "top" I see that there is a console running because the command is listed in the process list back in Gnome (Ctrl-Alt-F7). "who" shows me logged in on tty1.

Doing the following from this post, [http://ubuntuforums.org/showthread.php?t=454392&page=3](http://ubuntuforums.org/showthread.php?t=454392&page=3), fixes it:

1. sudo vi /etc/initramfs-tools/modules and add fbcon and vesafb
2. sudo update-initramfs -u
3. sudo vi /etc/modprobe.d/blacklist-framebuffer and 
   change the line "blacklist vesafb" to "# blacklist vesafb"
4. reboot and everything is fine 

Any ideas why I had to do this? What does this do exactly?
Thanks, this was an upgrade from the previous version of Ubuntu.

---

### Post by eznet on 2010-01-19
Did you ever figure out anything on this?  On my desktop, I can press CTRL+ALT+(F1 ... F6) and I just get a black screen.  CTRL+ALT+F7 brings me back into Gnome GUI no problem.  A bit frustrating due to being a CLI reliant user.  For now, I have to grab my laptop to ssh in and resolve whatever...

I am pushing my hardware with multiple headless vms, so sometimes I set something in a manner that may lock my system - dropping to shell is a must... stinks having to grab the lappy to get it done..

Running Karmic with SLI nVidia 8500 GTs... This very thing happened in Edgy with me and eventually was worked out with an upgrade - hope thats not the case this time...

Ideas anyone?  Much appreciation!

---

### Post by steveneddy on 2010-01-19
He gave his repair in the first post.

---

### Post by paalz on 2010-11-07
this is the right approach to solve this problem. in my case it worked but with some modifications, see here: [http://ubuntuforums.org/showthread.php?p=10085888#post10085888](http://ubuntuforums.org/showthread.php?p=10085888#post10085888)

---

