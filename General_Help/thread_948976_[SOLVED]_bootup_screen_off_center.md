---
title: "[SOLVED] bootup screen off center"
date: 2008-10-15
forum: General Help
---

### Post by xjgnsdof on 2008-10-15
To clarify, by "bootup screen" I mean the black screen with the Ubuntu logo and progress bar.

I installed Ubuntu with an external monitor plugged into the VGA port, and I think that's why the bootup screen is off center. How do I get it back to normal?

---

### Post by Partyboi2 on 2008-10-16
Have a look at your /etc/usplash.conf file and make sure that the xres  and yres settings are set correctly for your monitor.
eg 
> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1024
yres=768
 is for 1024x768 monitor setting.
If you need to make changes after the changes run in a terminal
```
sudo update-initramfs -k all -u
```

---

### Post by xjgnsdof on 2008-10-16
Solved. Thanks a lot.

---

