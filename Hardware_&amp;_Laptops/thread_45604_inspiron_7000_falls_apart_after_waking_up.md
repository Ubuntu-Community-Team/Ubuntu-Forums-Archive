---
title: "inspiron 7000 falls apart after waking up"
date: 2005-06-30
forum: Hardware &amp; Laptops
---

### Post by kerinin on 2005-06-30
i have two problems which materialize after i've put my laptop to sleep and then woken it up.

the first is that the wireless card which is installed via ndiswrapper doesn't work and causes a kernel panic if i try to fix it.  i think i can get around this by shutting down wlan0 and removing the ndiswrapper module before it goes to sleep.  is there a script or something which is executed prior to sleeping and after waking up? 

the second is that my usb plug stops working and i get a few hundred of these in my dmesg:

```
drivers/usb/input/hid-core.c: input irq status -84 received
``` 

any idea how to fix this?

thanks!

---

### Post by dgantony on 2005-07-01
I had the same issues. This is how I fixed them :

1) make a copy of the sleep.sh file
```
sudo cp /etc/acpi/sleep.sh /etc/acpi/sleep2.sh
```

2) open sleep.sh and replace all the lines with this
```
#!/bin/bash
rmmod ndiswrapper
/etc/acpi/sleep.sh
```

3) make a copy of the resume.sh file
```
sudo cp /etc/acpi/resume.sh /etc/acpi/resume2.sh
```

4) open resume.sh and replace all the lines with this
```
#!/bin/bash
/etc/acpi/resume2.sh
modprobe ndiswrapper
ifup wlan0
/etc/init.d/hotplug restart
/etc/init.d/dbus-1 restart

```

HTH

dgantony.

---

