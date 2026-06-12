---
title: "[SOLVED] Nvidia Drivers problems after upgrade"
date: 2008-11-21
forum: Hardware
---

### Post by ZeroZ400 on 2008-11-21
Hello,
I have a T61 with an Nvidia Quadro 140m video card.  I was using 8.04 and decided to upgrade to 8.10.  Upgrade went alright, until I did a logout and the screen went blank.  After the screen went blank, I tried switching to anther terminal but it wasn't responding so I powered the machine off.  After that I started getting problems with the nvidia drivers.  On bootup I get:

```
Ubuntu is running in low-graphics mode
(EE) NVIDIA(0): Failed to initialize NVIDIA kernel module! Please ensure that there is a
supported NVIDIA GPU in this system, and that NVIDIA device files have been created 
properly.  Please consult the NVIDIA README for detauks.  ***Aborting*** 
Screen(s) found, but none have a usable configuration
```

I tried following the menus to reuse my old configuration files which did not work.  I can boot up in low-graphics mode and deactivate the nvidia driver and work like that.  But, I want the nvidia drivers so I can use compiz and such.  

What do I need to do to get this resolved?

---

### Post by joseangelini on 2008-11-21
The nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04, are not compatible with the X.Org included in Ubuntu 8.10.The Nvidia driver could be installed through Envy package

---

### Post by ZeroZ400 on 2008-11-21
Problem was that the grub menu I was given after the upgrade was pointing to the wrong partitions.  So i took my backed up copy and overwrited the grub menu.  I added the current kernel to grub and now I'm able to boot.

---

