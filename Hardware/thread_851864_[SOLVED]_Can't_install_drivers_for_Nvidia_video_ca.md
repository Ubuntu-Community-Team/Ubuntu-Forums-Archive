---
title: "[SOLVED] Can't install drivers for Nvidia video card"
date: 2008-07-07
forum: Hardware
---

### Post by sideshowmel91 on 2008-07-07
```
sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a
                  Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```


Hardware Drivers list is blank.

```
sudo nvidia-settings
```
gives me this error: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

---

### Post by nikgare on 2008-07-07
Which card do you have?
Have you installed the drivers via synaptic?

---

### Post by sideshowmel91 on 2008-07-07
GeForce FX 5200
And I believe so.

---

### Post by nikgare on 2008-07-07
Can you be a bit more specific.
Which drivers did you install via synaptic, and what makes you think that they aren't installed?

---

### Post by sideshowmel91 on 2008-07-07
The problem seems to have fixed itself. Thanks though.

---

