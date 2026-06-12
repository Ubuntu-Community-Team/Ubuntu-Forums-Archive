---
title: "Removing desktop icons for mounted disks"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by kill4killin on 2007-07-05
Hey everyone,

I am running Ubuntu 7.04 and with Gnome desktop environment and was wondering about something (I hope I put this in the right place it was between this area and the desktop environments area so I apologize if I picked incorrectly). I noticed that whenever I put in a USB flash drive or a CD into my CD/DVD drive that an icon pops up onto my desktop to represent that mounted hardware. Well, I'm not a big fan of Icons on my desktop and so I would like to know how to get rid of this. I have the mount manager in my top panel so I can easily eject media from there and thus no longer have a use for the desktop icons. If someone could please inform me how to change the settings so that it doesn't do the icons when hardware is mounted I would really appreciate it. I tried googling for this a few times, but I wasn't quite sure what I was looking for...so even that would be helpful...

Thanks in advance

---

### Post by lawr_rawr on 2007-07-05
You can change that in configuration editor.

Alt-F2, gconf-editor, OK.

Go to apps/nautilus/desktop and uncheck volumes_visible. That should do it!

---

### Post by kill4killin on 2007-07-06
Ok thank you that worked just the way I wanted it to!

---

