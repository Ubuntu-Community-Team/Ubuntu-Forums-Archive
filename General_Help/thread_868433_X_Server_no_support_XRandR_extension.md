---
title: "X Server no support XRandR extension"
date: 2008-07-23
forum: General Help
---

### Post by knudsenjoe on 2008-07-23
Can't resize my desktop, I get this error:

The X Server does not support the XRandR extension. Runtime resolution changes to the display size are not available.

This is a reinstalled on this system, it worked before. I've got NVidia 'latest cards' driver. Any help would be greatly appreciated.

---

### Post by iaculallad on 2008-07-23
> **knudsenjoe said:**
> Can't resize my desktop, I get this error:

The X Server does not support the XRandR extension. Runtime resolution changes to the display size are not available.

This is a reinstalled on this system, it worked before. I've got NVidia 'latest cards' driver. Any help would be greatly appreciated.

Try to rebuild your xorg.conf file using the terminal command below:

```
sudo dpkg-reconfigure xserver-xorg
```

Once rebuild, log-off then log back on and try resizing your Desktop.

---

### Post by knudsenjoe on 2008-07-23
Ok, I did the reconfig, and now I have a 'banded' effect. There like stripes, and within these stripes they seem to fade from darker to lighter.

But now I can resize

---

### Post by iaculallad on 2008-07-23
Try re-configuring your NVIDIA settings:

```
sudo nvidia-settings
```

or

```
sudo nvidia-xconfig
```

As you've mentioned earlier, does: Latest card drivers = Restricted nvidia drivers?

---

### Post by knudsenjoe on 2008-07-23
I appreciate your help.

Sys>Admin>H'ware>'Nvidia latest cards' driver

doing sudo nvidia-settings returns:

   command not found

doing sudo nvidia-xconfig returns:

   Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.

   Device section "Configured Video Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---end by me---
Seems the driver is not in there, but I don't know how to put it there

---

