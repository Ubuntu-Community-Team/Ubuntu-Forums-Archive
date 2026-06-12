---
title: "Live USB 8.10 Default Safe Graphics Mode"
date: 2008-11-08
forum: General Help
---

### Post by wgcampbell on 2008-11-08
This post refers to the new 8.10 "Create a usb startup disk".  BTW, if you're using xubuntu, you need to install this option (apt-get install usb-creator).

I have an Intel 201GLY2A motherboard which doesn't like the default graphics drivers (higher resolutions display snow and vertical lines).  However, it works fine in "Safe Graphics Mode".

On this machine (low volume), I plan on using the Live USB stick rather than a hard drive install, so I needed a way to change the boot default.  I found that changes to the /etc/X11/xorg.conf file did not persist.

Anyway, I found that by editing the "text.cfg" file in your usb syslinux folder fixed the problem.  I added "xforcevesa" to the "append" line for the first (or default) menu option.

I have no idea if this is the correct way to change default boot options, but it worked for me and I thought it might help someone else.

---

