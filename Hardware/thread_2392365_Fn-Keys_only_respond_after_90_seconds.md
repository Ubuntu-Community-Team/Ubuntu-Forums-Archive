---
title: "Fn-Keys only respond after 90 seconds"
date: 2018-05-20
forum: Hardware
---

### Post by bluewolf42 on 2018-05-20
Hi,  I have an issue with my freshly installed Ubuntu 16.04 machine which drives me crazy. When pressing fn keys other than the volume keys and the sleep key (which work fine) it takes about 90 seconds until they are recognized. The brightness keys are most important for me but there's a wifi toggle key which would be desirable to work as well.   Some information about my system:  - Model: SP15-UMA (bought from a German company called "Tarox" which named this model "Modula Balance 1101810") - ```
cat /proc/cmdline: BOOT_IMAGE=/boot/vmlinuz-4.13.0-41-generic root=UUID=5952742c-bd2c-4737-a83b-a9d7607169e2 ro quiet splash vt.handoff=7
``` -```
 lshw -c video    *-display                       description: VGA compatible controller        product: Core Processor Integrated Graphics Controller        vendor: Intel Corporation        physical ID: 2        bus info: pci@0000:00:02.0        version: 18        width: 64 bits        clock: 33MHz        capabilities: msi pm vga_controller bus_master cap_list rom        configuration: driver=i915 latency=0        resources: irq:29 memory:fb000000-fb3fffff memory:c0000000-cfffffff ioport:f080(Größe=8) memory:c0000-dffff
``` -```
 ls /sys/class/backlight/ acpi_video0  cmpc_bl
```  Adjusting the brightness via the gui works as well as manually writing something into /sys/class/backlight/acpi_video0/brightness. The strange thing is, it worked when I first logged in after the fresh install, but after suspending to ram and resuming it's broken even after restarting the system. Same story with the Ubuntu live system I used for installing.  What I don't understand is that my system only has an Intel graphics controller but there is no /sys/class/backlight/intel_backlight folder (but I don't know much about that stuff). Even more, within the xorg.conf.d folder there are two files suggesting that there is AMD hardware present: ```
]ls /usr/share/X11/xorg.conf.d/ 10-amdgpu.conf  10-radeon.conf ...
```  I already tried adding the acpi_osi=linux toggle in grub as well as every option for acpi_backlight (vendor, native, none, legacy, video) but nothing worked.  With one of these settings (I think it was "native" or "none"), only cmpc_bl was present in /sys/class/backlight. After changing the brightness via the gui the system was totally freaking out as it randomly changed the brightness every few moments.   After hours of searching and testing I'm quite desperate and would reeaally appreciate some help. If you need any additional info just tell me.   Thanks

---

### Post by bluewolf42 on 2018-09-18
Has really nobody an idea?

---

### Post by QIII on 2018-09-18
Hello!

Taking several months to bump your post is a sure way to let it sink to the bottom of the sea -- never to be found.  People rarely go looking through muck that deep.

After about 12 hours, a thread gets buried.  If you have gotten no response in that time, feel free to bump your thread.

Cheers!

---

### Post by bluewolf42 on 2018-09-20
Well, yeah, I kind of lost track of it... But thanks for the information!   But I'm still interested in getting that problem solved.

---

