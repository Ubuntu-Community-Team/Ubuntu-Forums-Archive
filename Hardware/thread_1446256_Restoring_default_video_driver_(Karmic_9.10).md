---
title: "Restoring default video driver (Karmic 9.10)"
date: 2010-04-03
forum: Hardware
---

### Post by happysadhu on 2010-04-03
Hi,
I installed the proprietary nvidia driver through the hardware drivers GUI, now my c840 Dell laptop screen won't boot up. It just remains blanc. I want to restore the  driver to the default open-source one which worked.

Can I do this through the command-line in recovery-mode? Or, how can I start up the desktop in low graphics mode and deactivate the proprietary nvidia driver?

Thanks,
Sam

---

### Post by kblft on 2010-04-03
If you can get a command line in recovery mode - you can edit xorg.conf to load the vesa driver (which is the default before installing drivers) instead of the nvidia one.

```

# make backup of xorg.conf
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bck

# edit xorg.conf
nano /etc/X11/xorg.conf

```

Change the value of the Driver from "nvidia" to "vesa" and try to reboot your computer and see if X loads

You can also do apt-get purge on the nvidia packages 

I'm not in front of my ubuntu machine right now so the instructions are a little offhand - still, I hope it will do...

---

### Post by happysadhu on 2010-04-03
Hi,
Thanks for your quick reply! I was able to reset to the default driver simply by deleting the xorg.conf as in:
sudo rm /etc/X11/xorg.conf

If there is no xorg.conf file, Ubuntu generates a new one.

Sam

---

