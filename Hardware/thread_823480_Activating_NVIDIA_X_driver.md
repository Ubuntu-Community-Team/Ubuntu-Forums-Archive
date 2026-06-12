---
title: "Activating NVIDIA X driver"
date: 2008-06-09
forum: Hardware
---

### Post by Maestrom on 2008-06-09
Hi,

Seems I'm having the same issues a lot of people are having with Ubuntu 8.04.  I'm running an NVidia GeForce 7300 Go on my laptop and getting told I can only run in low resolution mode.  I saw in one of the forum threads that I could install EnvyNG, so I did that and had it reinstall my NVidia driver (I uninstalled the old one first).  I still can't get out of low resolution mode, however, I have found that when I go to System - Administration - NVIDIA X Server Settings I get this message:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." 

Could editing my X configuration file be the solution to my low resolution problem.  If, how do I do this.  I am relatively new to using Linux and don't understand how/am afraid to play with anything in my root, so if this is a possible solution could someone please tell me how to do this.

Thanks

---

### Post by Vadi on 2008-06-09
Try going to system - administration - hardware drivers, and enabling the video driver. Does that help you?

---

### Post by Maestrom on 2008-06-10
No.  I already did that and it said it is enabled, but I'm still stuck in low-resolution mode and when I open the NVIDIA X Server Settings I still get the same message.

---

### Post by Vadi on 2008-06-10
Try disabling/enabling it? That's strange.

---

