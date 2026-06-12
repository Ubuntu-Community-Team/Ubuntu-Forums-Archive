---
title: "Intrepid upgrade- can't save nvidia xconfig"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by kolibri on 2008-12-05
I upgraded to intrepid.  

Hardware drivers says that NVIDIA driver 1.77 is activated and currently in use.

When I try to start NVIDIA X server settings it says 
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

Sudo nvidia-xconfig gives me :
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

However, when i restart the x server, or when i restart the system, it still won't let me access the NVIDIA X-server settings, and I start the loop above again.

This happened on one of my last upgrades, and I don't remember how I fixed it.  I think just running envy worked then.  I see others having the same problem, but none of those threads seem to solve the issue.

---

### Post by KEE on 2008-12-05
anyone ?

---

### Post by kolibri on 2008-12-05
I've tried installing the latest driver direct from NVIDIA, i've tried reinstalling from ENVY, I've tried some of the suggestions on the buglogs, but I still get:

failed to initialize the NVIDIA graphics device
....
Run Ubuntu in low graphics mode



when I turn on the computer.

---

### Post by Sam Lars on 2008-12-06
What kind of card do you have?
I'm having similar trouble with a 5200.

---

### Post by kolibri on 2008-12-12
I have a Nvidia GeForce 7300 GS, which  nvidia-glx-177 is supposed to support.  I just installed the latest Intrepid updates which included some NVIDIA modelalias updates, but nothing has changed.  

When i turn on the computer I still get: 

-----------
Failed to initialize the NVIDIA graphics device
...
Run Ubuntu in low graphics mode
-------------------

Once I'm logged in the hardware drivers says that NVIDIA driver 177 is activated and currently in use.

When I try to start NVIDIA X server settings it says
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

Sudo nvidia-xconfig gives me :
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

However, when i restart the x server, or when i restart the system, it still won't let me access the NVIDIA X-server settings, and I start the loop above again.

---

