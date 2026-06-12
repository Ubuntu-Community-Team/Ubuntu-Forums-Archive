---
title: "Plugging in USB Camera Causes System Lockup"
date: 2004-12-24
forum: Hardware &amp; Laptops
---

### Post by Kick The Donkey on 2004-12-24
When I plug in my USB digital camera, my entire system locks up.  I'm running Ubuntu 4.10.  My camera is a Fuji FinePix 1300.

Any ideas how I can track down what's going on?

---

### Post by Kick The Donkey on 2004-12-29
Has anyone ever run in to this?

---

### Post by hardcandy on 2004-12-29
"/dev/sda1        /mnt/usb        vfat   defaults,noauto,users,sync,umask=0022      0 0" probably needs to be added to "/etc/fstab". Be sure and make the /mnt/usb (or /mnt/camera, etc) directory. 

from 
[Working With USB Devices in Linux](http://tlug.up.ac.za/csslug/usb_devices.html)  Excellent resource.

---

### Post by dave_euser on 2004-12-29
[QUOTE=Kick The Donkey]Has anyone ever run in to this?[/QUOTE]
 If this is still happening, maybe try running "tail -f /var/log/messages", then plugging in the camera and see if anything interesting occurs....

---

### Post by animalstyle on 2004-12-29
I disabled Legacy USB support in my BIOS, and all my hotplugging came to life.  Im happy now.  Of course, if your Camera isnt USB 2.0, i dont know what to say.

---

