---
title: "Startup-script for HP LserJet 1000"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by Ollan on 2005-09-15
I need to run the following command at startup.
"cat /opt/foo2zjs/sihp1000.img > /dev/usb/lp0"

The problem is that I get "Access denied" if i run the command in the terminal. Even if i write "sudo cat /opt/foo2zjs/sihp1000.img > /dev/usb/lp0". If i change the right to 662 for lp0 its possible to load the firmware to lp0 in the terminal.

How create a working script?

---

### Post by mlomker on 2005-09-15
That's an odd problem.  You could edit the /etc/udev/permissions.d/udev.permissions file to assign the /dev/lp0 device a different set of permissions at start-up.  

I think you'll want to change this line to read 0666.

```

usb/lp[0-9]*:root:lp:0660

```


Then you could add your cat command to the end of /etc/init.d/bootmisc.sh.

---

