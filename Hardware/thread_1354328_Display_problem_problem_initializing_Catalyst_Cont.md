---
title: "Display problem: problem initializing Catalyst Contol Center Linux edition..."
date: 2009-12-13
forum: Hardware
---

### Post by Wilabob on 2009-12-13
Hi I'm trying to use the Display configuration thing under system > preferences. When I click it it says: "It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?" 

When I click yes it says: "Initialization Error
There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following:
No ATI graphics driver is installed, or the ATI driver is not functioning properly. Please install the ATI driver appropriate for your ATI hardware, or configure using aticonfig."

When using the lspci command in terminal it says my video card is Intel Corporation 82810 (rev03.) This is the built in card. I have a CUW-RM motherboard. What do I need to do to get this working? I would like to use a higher resolution with ubuntu. My installation of windows xp can go to 1280 x 800 if not higher. Please help me with this problem! Thanks

---

### Post by Wilabob on 2009-12-13
OK, I was able to get past that by clicking no but when I get to the display config I can only use up to 1024 x 768. I read around and saw some things on editing the xorg.conf file but ubuntu 9.10 doesn't use this... What can I do to get more resolutions?

---

### Post by Wilabob on 2009-12-13
OK, got furthur... I followed this guide: [http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)
But when I try to change resolution I get: The selected configuration for displays could not be applied could not set the configuration for CRTC 68. Please help! I'm so close!

---

