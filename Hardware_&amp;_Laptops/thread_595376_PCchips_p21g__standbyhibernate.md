---
title: "PCchips p21g  standby/hibernate"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by rfm33428 on 2007-10-28
I have a PCchips motherboard P21g,   For the most part I have no problems with Ubuntu.  However standby & hibernate don't work.   Standby seems to work, but when I reactivate my computer, it reboots everything & during the process Ubuntu freezes until I restart again.   Hibernate seems to work also, but when I turn on my system, Ubuntu freezes during the boot process & I have to reboot again to get Ubuntu to load up.   Any suggestions?

---

### Post by rfm33428 on 2007-10-29
Anyone that might be reading this, I finally got my suspend & hibernate to work.  I had to make changes to a couple of files.   They are:

file /etc/default/acpi-support

ACPI_SLEEP=true        
ACPI_SLEEP_MODE=standby
MODULES="agpgart"        
SAVE_VBE_STATE=false        
POST_VIDEO=false        
USE_DPMS=false

file /etc/X11/xorg.conf 

Section "Device"
    Driver       "nvidia"
      ...
    Option      "NvAGP"  "1"
EndSection

I found this from a post by kornelix and I also saw similar posts too by others.

---

