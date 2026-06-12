---
title: "Networking and Menu"
date: 2005-11-24
forum: General Help
---

### Post by splinterz on 2005-11-24
1) System->Administration->Networking menu is gone, how can i get it back?

2) my laptop works fine at home when plugged into my router, but i cannot connect at the university i attend. i've tried setting up a static ip address, but that doesn't seem to help. i know the network is ok because my friend can connect his laptop (also running ubuntu) to the network without problems. point me in the right direction?

3) could 1 be related to 2?

thanks! 

my apologies if the previous questions have been answered somewhere else, i've searched the forums but have not found solutions.

---

### Post by not_yet on 2005-11-25
try this

right click menu bar / add to panel / main menu

---

### Post by splinterz on 2005-11-25
nope it didn't work. i still have the System->Administration menu, but this is all that's in it:

- Add Applications
- Device Manager
- Login Screen Setup
- Printing
- Synaptic Package Manager
- Update Manager

---

### Post by Randy Sparks on 2005-11-25
The program you're talking about can be run from the command line as 

gksudo network-admin

If you type that, does the program run? If so, why not just create a new shortcut/launcher?

---

### Post by splinterz on 2005-11-25
when i run that command i get an error stating that the command not found, and a pop-up stating that:

Failed to run network-admin as user root:
Child terminated with 1 status

---------------------------------------------------------------------------

however, i found that network-admin is part of the gnome-system-tools, and reinstalling it has brought back all my missing menus. :)

so, any ideas on my university network situation?

---

