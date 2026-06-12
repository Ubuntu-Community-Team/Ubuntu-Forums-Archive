---
title: "Oops... I accidentally deleted /etc/modprobe.d/options"
date: 2009-01-21
forum: Hardware
---

### Post by Joebaynham on 2009-01-21
While trying to gain root access to '/etc/modprobe.d/options' to get it to allow audio after being awaken I accidentally deleted the file, how do I get it back xD?
Sorry I am a complete newb..

---

### Post by taurus on 2009-01-21
See if there is a backup version first.

```
ls -la /etc/modprobe.d
```
Otherwise, here is my version so modify it for your machine.

```

# /etc/modprobe.d/options
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# Stop auto-association.
# LP: #264104
options ipw2200 associate=0

# XXX: Ignore HPA by default. Needs to be revisted in jaunty
options libata ignore_hpa=1

```

---

