---
title: "Graphics in Ubuntu not supported"
date: 2008-10-07
forum: General Help
---

### Post by Spydr13 on 2008-10-07
So, I have a perfectly working version of Ubuntu on my laptop, but it's not working at all on my desktop.  I installed it, updated it to 8.04, then, when I restarted, it said graphics mode not supported.  I can get to a terminal through the alt+ctrl+f1 command, but that's about it.  I have an ATI graphics card on desktop, which I heard has poor linux support, the nvidia on my laptop works perfectly though.  

Let me know if there's any information you need to help me figure out this problem.  Have to go to sleep now though, will check tomorrow morning before I leave.  Just let me know everything I have to do and all the information I need to get in like one post, and I'll add it tomorrow.  

Any help would be appreciated.  Thanks =P

(Also, if another version of Ubuntu works better with an ATI graphics card, let me know, and I'll gladly switch over.)

---

### Post by 3rdalbum on 2008-10-07
Did you start from 7.10 and update it to 8.04? If you have used Envy on 7.10, you must visit the Envy website and follow the instructions there about what to do after upgrading to 8.04.

This should get you up and running: (put this into the terminal that you get through control-Alt-F1)

```
sudo nano /etc/X11/xorg.conf
```

Under Section "Device", change the driver to "vesa". Save your changes and exit by pressing Control-X, then Y, then the Enter key. Reboot ("sudo reboot") and see what happens. If it doesn't help, you might need to remove some of the resolutions under Section "Screen".

---

### Post by der_hede on 2008-10-07
There should be some old /etc/X11/xorg.conf.X file to start with (an old backup where X is some string, for example a number representing a date).

Simply copying the original backuped xorg.conf file should be the best to start with.

Or use "sudo dpkg-reconfigure xserver-xorg" to rewrite your xorg.conf with some default one.

---

### Post by Spydr13 on 2008-10-07
> **der_hede said:**
> There should be some old /etc/X11/xorg.conf.X file to start with (an old backup where X is some string, for example a number representing a date).

Simply copying the original backuped xorg.conf file should be the best to start with.

Or use "sudo dpkg-reconfigure xserver-xorg" to rewrite your xorg.conf with some default one.

The "sudo dpkg..." command worked.  Thanks bro =P

---

