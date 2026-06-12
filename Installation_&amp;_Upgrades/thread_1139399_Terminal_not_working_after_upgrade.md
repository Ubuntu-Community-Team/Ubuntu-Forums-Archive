---
title: "Terminal not working after upgrade"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2009-04-27
I just upgraded my system from 8.10 to 9.04 and everything seems to be OK so far except I seem to have lost my terminal.
When I try to start the terminal I get the usual box, but its completely blank and an error message "There was an error creating the child process for this terminal"
Any ideas?

---

### Post by tcmartin24 on 2009-04-27
I too am experiencing this same problem as a result of having upgraded from 8.10 to 9.04.

---

### Post by sahabcse on 2009-04-27
Try alt+f2 Type gnome-terminal

---

### Post by Stolea on 2009-04-27
> **sahabcse said:**
> Try alt+f2 Type gnome-terminal
That produces the same result.
Any ideas how to get my terminal back again. I am missing it.

---

### Post by sahabcse on 2009-04-27
Try to reinstall gnome-terminal from synaptic

---

### Post by Stolea on 2009-04-27
This seems to be not the only problem. I just had a full lockup of the system and synaptic just sits there and spins its wheels.
I will do a full fresh install. 
Bummer.

---

### Post by sahabcse on 2009-04-27
Press alt+ctl+f1 there

sudo apt-get purge gnome-terminal
sudo apt-get install gnome-terminal

---

### Post by Stolea on 2009-04-29
Thanks, I just did a clean install of the 64 bit version. It would appear to have overcome the shortcominings of the 8.04 version which had issues with my ATI card.
Cheers

---

