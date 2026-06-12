---
title: "/dev/ttyUSB"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by Flane on 2005-08-09
Hi,

i'm currently working to get my palm handheld sync with kpilot.
i found this tutorials with udev and /dev/pilot, but as far as i understood there should be all the time some links like

/dev/ttyUSB*

But in my current setup there aren't any files. So do i need a special kernel switch oder something for this entries to exist?

Thanks a lot

Flane

---

### Post by Juergen on 2005-08-09
> there should be all the time some links like /dev/ttyUSB*Not all the time, just after you press the sync-button, and only until sync is over.

Open a xterm and try```
tail -f /var/log/messages
```and then press the sync-button. You should see some messages about the device-nodes being created.

---

### Post by Flane on 2005-08-09
hi,
i solved the problem.
i needed to configure my custom kernel to use the visor module.
after having the visor module installed i managed to create a udev rule to create the /dev/pilot and now everything works

thanks a lot for your help

Flane

---

