---
title: "Can't get nVidia drivers to work"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by Crusty on 2005-08-03
I recently upgraded from Warty to Hoary using apt-get. Everything seemed to go smoothly, but when I rebooted X wouldn't start. I tried downloading the nVidia drivers through apt-get and got no errors while doing it. I ran nvidia-glx-config enable and it said everything was hunky-dory, but still no go. If I switch the driver back to "nv" in my xorg.conf file, it will run.

If I run cat /proc/drivers/nvidia/agp/status, it tells me "nvidia" is disabled. I'm not sure how to enable it.

If anyone needs my xorg.conf file or anything else, let me know.

By the way, I had the Ubuntu nVidia drivers working fine in Warty. Not sure why it won't work now.

---

### Post by TravisNewman on 2005-08-03
It seems that the module may not be loading. Try changing the xorg.conf back to nvidia, then "sudo modprobe nvidia" then starting gdm again. If that works, edit /etc/modules and add "nvidia" at the bottom.

---

### Post by Crusty on 2005-08-04
I tried your suggestion but it didn't work.  :???: The screen blinks a few times while it tried to get X started and then stays black until I press a key. Then it tells me it couldn't start X. When I look at the error it gives me, it says

> Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o": No symbols found

---

### Post by Crusty on 2005-08-04
Eureka! I got it to work by downloading the linux headers for my kernel, then removing and reinsalling the nvidia driver. I should've thought of that earlier.

---

