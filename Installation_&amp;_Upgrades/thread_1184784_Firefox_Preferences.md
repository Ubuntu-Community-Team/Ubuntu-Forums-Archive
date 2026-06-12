---
title: "Firefox Preferences"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by stonehouse on 2009-06-11
I am unable to launch Firefox and have it default to my saved preferences/add-ons.  I have an awkward workaround that works by launching Firefox with a "sudo" prefix.  Without running it with root privileges, it will only run in a partially installed mode and will not resave any preferences, add-ons, etc.  This has been going on for several months now.  Can anyone help?? - much appreciated.  (Note - Ubuntu 9.04, Firefox 3.0.10)

---

### Post by oldsoundguy on 2009-06-11
uninstall Firefox and install it from synaptic or add/remove.  Then go into applications> internet> and drag and drop the icon to your panel (I have other things that I use all the time there also).  That will give you a quick launch of the program.

---

### Post by drs305 on 2009-06-11
You may not have privileges to write to your default profile. Try starting firefox with "firefox -p" and creating a new profile. Make sure the profile's location is somewhere in your $HOME folder or another folder you own.

You can also find the default profile that is not working and check the permissions of that folder. If you can find it, make sure you are the owner and have r/w privileges.

---

### Post by stonehouse on 2009-06-14
Thankk you DRS305.  The new profile fixed the problem but it took nearly 2 days to re-set all my preferences and add-ons to their previous state.  I was unable to copy them from the other profile.  Also, wiping out firefox and re-installing didn't change my previous problem.  Thanks for the help.

---

