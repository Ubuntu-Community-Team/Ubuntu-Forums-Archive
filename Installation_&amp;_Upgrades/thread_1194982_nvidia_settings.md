---
title: "nvidia settings"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by nixIT on 2009-06-23
Hello all, 

I have a Dell Latitude D830 plugging into a docking station.  All is working correctly, except when I reboot, that is when my Dell 24" monitor goes into standby.  I open the lid on my laptop, log in, go to the nvidia settings and adjust my display to get my 24" set.  I then try to Save to Xorg.conf and I get the following error:

"Failed to parse existing X config file '/etc/X11/xorg.conf'!"

I even ran the following:

```

sudo nvidia-settings

```

and got the same thing.  Is there a way to save these setting to my xorg.conf file?  

--nixIT

---

### Post by systemgod on 2009-06-23
Try removing your /etc/X11/xorg.conf file (make a backup first!!!). Then try running the NVIDIA tools again, it should create a new xorg.conf.

Note: I had to temporarily change ownership of /etc/X11 to myself otherwise the NVIDIA tool couldn't write to xorg.conf (and couldn't create a backup, changin ownership of xorg.conf alone wasn't good enough)

Nico

---

### Post by nixIT on 2009-06-23
> **systemgod said:**
> Try removing your /etc/X11/xorg.conf file (make a backup first!!!). Then try running the NVIDIA tools again, it should create a new xorg.conf.

Note: I had to temporarily change ownership of /etc/X11 to myself otherwise the NVIDIA tool couldn't write to xorg.conf (and couldn't create a backup, changin ownership of xorg.conf alone wasn't good enough)

Nico

I tried that, and ran nvidia-settings as sudo, but I got a message that said couldn't open xorg.conf.

Not having much luck with 9.04.  :(

--nixIT

---

