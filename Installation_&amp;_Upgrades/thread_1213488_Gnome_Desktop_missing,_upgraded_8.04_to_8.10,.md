---
title: "Gnome Desktop missing, upgraded 8.04 to 8.10,"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by danebramaged on 2009-07-14
I installed Hardy Heron 8.04 from disk and, upgraded to Intrepid Ibex 8.10 flawlessly.  
I uninstalled evolution mail and installed thunderbird.  I also uninstalled a mail notification program.  

The mail notification program started asking for access to the evolution "key ring" or some such thing which I didn't quite get.  So I canceled out of that and restarted the computer since I had already (cleanly) uninstalled the program and, figured it was just still sitting in memory.

When the computer came up I got the logon screen and sound.  Everything looked fine.  

I logged in, got wall paper and more good sound, and no interface.  I'm running Gnome.
Since compiz was configured, I can still use the mouse to turn my wall paper into a cylinder and I can mount and unmount my sandisk thumb drive.

Please help.

How do I get my interface back?  


Thanks in advance, who ever you may be.

---

### Post by danebramaged on 2009-07-15
[Solved]

When I uninstalled evolution mail, it took out a lot more than just evolution mail.  It also removed gnome.

Faced with nothing but wall paper to look at;

I right clicked on the desktop and created a new folder.

I clicked on the folder and got the nautilus? (explorer) file browser.

I typed the word "terminal" in the search bar.

I scrolled way down to the "terminal" icon.

I clicked on the terminal icon and at the command line typed in the following;

sudo apt-get install gnome

A reboot of the system brought everything back.

whew.

---

