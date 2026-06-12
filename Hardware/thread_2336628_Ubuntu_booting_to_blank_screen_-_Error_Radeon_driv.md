---
title: "Ubuntu booting to blank screen - Error Radeon drivers"
date: 2016-09-09
forum: Hardware
---

### Post by kristinaa on 2016-09-09
I installed Ubuntu on a crappy HP laptop a few weeks ago and then spent a lot of time this week installing LAMP and Laravel, SSH etc for a new project.  
Version:  Ubuntu 16.04 Xenial Xerus,
Everything worked fine up until today when I tried to boot up and just getting a blank screen.
Booting from USB stick works great so hardware is fine.
Tried boot repair tool and as expected did not help.  
Editing video mode boot options in GRUB does not help.
Other issues with drivers seem to include Ethernet cable not detected.  

Error in Radeon driver not loading.  Gnome showing as not installed?

Any tips or ways to try to fix, greatly appreciated.

---

### Post by kristinaa on 2016-09-10
update: definitely determined that it has something to do with "no screens " being recognized when trying to start the GUI.  examined the startx error log.  Do I need to reinstall the Radeon drivers?  Ethernet cable is now being recognized and I ran dist-update.

---

