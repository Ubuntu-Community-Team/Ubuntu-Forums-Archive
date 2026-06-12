---
title: "Nvidia Driver"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by FleaBR on 2007-04-25
I installed the proprietary driver trough the restricted drivers section but i dont have 3D Aceleration nor OpenGL support, i can't even change my resolution to 1280x1024 75Hz =/

Edit: It's a 7600GT

---

### Post by robenroute on 2007-04-25
I had similar problems. What happened is that choosing the restricted manager, resulted in the removal of nvidia-glx-new. The restricted manager just installed nvidia-glx again. Result: couldn't even start X again. What I did: from the command line, I removed nvidia-glx and installed nvidia-glx-new again. Then edited (make a backup first!) the xorg.conf file for the resolution settings were off. After a reboot, I had to change the resolution from the System menu (Preferences, Screen resolution) and presto, everything was good again.

Hope this helps.

---

