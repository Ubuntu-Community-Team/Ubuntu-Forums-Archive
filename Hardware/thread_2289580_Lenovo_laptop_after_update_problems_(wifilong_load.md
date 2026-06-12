---
title: "Lenovo laptop after update problems (wifi/long loading time)"
date: 2015-08-05
forum: Hardware
---

### Post by Artemio_T on 2015-08-05
Hello, I have a couple of issues with my laptop after updating my system:
Lenovo S510p
Nvidia Geforce
12gb Ram
Ubuntu 15.04

1. It has begin to taking a lot of time to load after update (it was very very fast on previous kernel)
2. Sometimes it doen't load the wi-fi module, and I cannot start it from control panel, after rebooting one of two times starts to work again.

I'va installed and uninstalled firestarter, after that I've got new error while loading
Job sockets.target/start deleted to break ordering cycle starting with basic.target/start
Job firestarter.service/start deleted to break ordering cycle starting with basic.target/start

while trying to install firestarter it says:
(firestarter:4202): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-30vEHzfW5a: 

I guess this may be relevant with wi-fi
Also I have these new errors:
vgaarb: this pci device is not a vga device
```

ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   32.689564] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   32.689620] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   32.689681] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   32.689749] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   32.689800] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   32.689905] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   32.689957] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   32.789452] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   35.268585] vgaarb: this pci device is not a vga device



```


I guess this is related to loading time.
While system is loading I see that my cpu is loading about 100% but can't see any process what uses it in system monitor

Results of dmesg are here [http://paste.ubuntu.com/12005893/](http://paste.ubuntu.com/12005893/)

So here are summery of questions:
1. Firestarter and D-BUS daemon , gives errors while installing
2. Wi-fi sometimes working sometimes not
3. After update loading takes more more time

---

### Post by MikeCyber on 2015-08-05
Often after an update you need to reinstall the proprietary graphics drivers.

---

### Post by Artemio_T on 2015-08-05
done, not helped

---

### Post by Artemio_T on 2015-08-06
no ideas?

---

