---
title: "nVidia Driver Stopped Working"
date: 2009-03-13
forum: Hardware
---

### Post by HDTimeshifter on 2009-03-13
A few days ago, my PC started going into hibernation and not waking up unless I rebooted.  After several reboots, it now starts up in low resolution and when I try to reset the resolution through System/Administration/nVidia X Server Settings menu, it tells me
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

I tried that, however get the following error:
sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by HDTimeshifter on 2009-03-13
Simply rebooting wouldn't fix it, but I copied a version with what looked like the date appended to the file name back to /etc/X11/xorg.conf and rebooted and am now able to set my screen resolution through the nVidia menu tool.

---

