---
title: "[SOLVED] uswsusp loses not used usb ports after resuming."
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by rumo_orbis on 2007-11-26
ok... firstly i have to say xubuntu 7.10 rocks... basically now (after recompiling kernel everything works... fglrx, ndiswrapper, suspend + hibernate, even my wireless network printer it found without having to manually do anything)...
but there's one problem remaining. after hibernate/suspend (s2disk/s2both) with uswsusp it seems only the usb ports that have been used before suspension work after resuming. all the others don't work at all, which means that i can't plug in any additional devices. i really have no clue what's causing that and would be extremely glad to get that solved. basically it's what's in between me and my first perfect linux laptop :P.

any help would be really appreciated!

rumo

---

### Post by rumo_orbis on 2007-11-27
bump

---

### Post by rivera151 on 2007-11-27
Edit the /etc/hibernate/common.conf.  Uncomment the UnloadModules line, and make it so that your USB kernel module gets unloaded (EG UnloadModules kernel-module-name).  You can find out what module runs your USB using the System-->Preferences-->Hardware Information, program by selecting your USB, and looking at the info.linux.driver entry.  Make sure that the "LoadModules auto" entry is also uncommented.  See if that helps.

---

### Post by rumo_orbis on 2007-11-27
that file doesn't seem to exist on my computer... neither does the folder "hibernate".
any ideas?

---

### Post by rivera151 on 2007-11-27
Install hibernate: "sudo apt-get install hibernate"

Then check again.

---

### Post by rumo_orbis on 2007-11-28
thanks for trying to help me! but when using the hibernate script neither usb nor my wireless card (with ndiswrapper) worked after resuming. but i got another idea. i just wrote a little script to rmmod and modprobe ehci_hdc (my usb module) during each resume. i know it's not a very elegant solution, but at least it works. :)

thanks a lot anyway!

---

### Post by rivera151 on 2007-11-28
> **rumo_orbis said:**
> I just wrote a little script to rmmod and modprobe ehci_hdc (my usb module) during each resume. i know it's not a very elegant solution, but at least it works. :)

thanks a lot anyway!

That would do it!  Good to know you got it done.  Have fun.

---

