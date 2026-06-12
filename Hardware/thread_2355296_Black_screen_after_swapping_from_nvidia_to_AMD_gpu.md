---
title: "Black screen after swapping from nvidia to AMD gpu"
date: 2017-03-11
forum: Hardware
---

### Post by jumpingclear on 2017-03-11
I recently got a new AMD graphics card. My previous card was Nvidia. I don't use ubuntu so much these days and forgot about it prior to installing the card. I had been running the proprietary nvidia drivers.

With the new card ubuntu boots to a black screen as I assume it is trying to use the old nvidia drivers. I can get to a console.

What do I need to do from the console to fix the problem? I want to try the open AMD drivers. I assume uninstall the proprietary nvidia drivers but I am not sure what packages I need to uninstall. Then do I need to install the open amd drivers or set them up in any way or will they be picked up automatically?

thanks

---

### Post by oldrocker99 on 2017-03-11
Try this:```
sudo apt-get remove --purge nvidia*
```

This will remove the nVidia drivers and all the config files. Reboot afterwards. The open-source Radeon driver should already be installed.

---

### Post by jumpingclear on 2017-03-19
Thanks for the reply. That solved it :)

---

