---
title: "MSI Wind U100 Trackpad issue"
date: 2008-11-19
forum: Hardware
---

### Post by digen on 2008-11-19
Hello,

I recently upgraded Ubuntu ( 8.04 ) to 8.10 on my MSI Wind U100 Notebook. After successfully upgrading the trackpad doesn't work anymore. It works till the point the login credentials are entered at the Gnome login screen. After logging in trackpad is in frozen state and there are no movements whatsoever in any direction. 

The relevant part in /etc/X11/xorg.conf is as follows,

Section "InputDevice"
         Identifier          "Synaptics Touchpad"
         Driver               "synaptics"
         Option                "SendCoreEvents"     "true"
         Option               "Device"              "/dev/psaux"
         Option                "Protocol"            "auto-dev"
         Option                "HorizEdgeScroll"      "0'
EndSection

Anyone else facing this issue ? Any input is much appreciated. Thanks !

---

### Post by Saghaulor on 2009-01-02
From what I 've gathered, the Wind touchpad doesn't use the synaptics drivers.

Please see these threads, perhaps they'll offer more help.

[http://ubuntuforums.org/showthread.php?t=961324&highlight=msi+wind](http://ubuntuforums.org/showthread.php?t=961324&highlight=msi+wind)

[http://ubuntuforums.org/showthread.php?t=977046&highlight=msi+wind](http://ubuntuforums.org/showthread.php?t=977046&highlight=msi+wind)

---

