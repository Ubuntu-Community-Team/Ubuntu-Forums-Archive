---
title: "Uninstall Ubuntu"
date: 2008-09-27
forum: General Help
---

### Post by Sirugel on 2008-09-27
I wanted to uninstall ubuntu, but everytime I clicked the uninstaller it didn't open. So I went into Program files and deleted everything in the Ubuntu folder except the uninstaller ( to be safe )

But when i restarted my computer the win vista and ubuntu dual boot window still came up


How do I get that off?

---

### Post by kokkus on 2008-09-27
First of all, you didn't remove ubuntu (You destroyed it).
Remove the partition ubuntu is installed on.
Ubuntu will then remove it self from grub.
If not, you can go into windows and download and install Auto Super Grub Disk 1: [http://www.download.com/Auto-Super-Grub-Disk/3000-2094_4-10829335.html?tag=mncol&cdlPid=10829336](http://www.download.com/Auto-Super-Grub-Disk/3000-2094_4-10829335.html?tag=mncol&cdlPid=10829336)

---

### Post by Predator106 on 2008-09-27
Don't forget to resize the partition that windoze resides on, so you can regain the space.

---

### Post by howefield on 2008-09-27
The way the OP has worded it, sounds more like a Wubi install ? as opposed to an install with real partitions.

If that's the case I'd put it back on and try again via add/remove programs in control panel.

---

### Post by alzie on 2008-09-27
Is this a dual boot situation where you formatted a drive and installed Ubuntu onto it or is this a Wubi installation?

If it was a Wubi install You should be able to find a solution here: [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

Since you have manually removed parts you may need to "install" wubi again in order to remove it properly.

I hope this helps.

<edit> If you use this link, scroll up and there is more information on removing Wubi using add/remove or Uninstall-Ubuntu.exe if that doesn't work.

---

### Post by Predator106 on 2008-09-29
> **howefield said:**
> The way the OP has worded it, sounds more like a Wubi install ? as opposed to an install with real partitions.

If that's the case I'd put it back on and try again via add/remove programs in control panel.

Yeah, you're probably right, I was wondering about that, but then assumed that the guy above me understood him more than me. I hate it when I always think I'm wrong :)

---

