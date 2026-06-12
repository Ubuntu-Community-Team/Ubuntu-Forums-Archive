---
title: "external display no longer detected after reboot"
date: 2016-09-23
forum: Hardware
---

### Post by Matthieu_van_Kints on 2016-09-23
Hello, 

since a month or two i have a external monitor (Samsung Syncmaster 2493hm) connected to my laptop (Asus f551m) via hdmi cable. 

since ubuntu runs very stable i rarely reboot but for one reason i can't recall i decided to leave it of during the night. 
since the boot the very next morning the monitor isn't detected anymore. 

neither automatically, nor via detect monitors in system settings/monitors. 

first time i plugged the monitor in it worked immediately and nothing happend physically with either the monitor, laptop or hdmi cable, just a turn off and turn on. 

sudo lshw -c display gave: 
                      
```
  *-display        
       description: VGA compatible controller
       product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:91 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8)

```

i swapped the hmdi cable with another one (brand new, not tested and have no means to test it) but without effect

display scans all ports but doesn't find a signal and displays "check signal cable". 

am not sure what extra info to give you guys to help you help me. so please ask if unclear or uncompleet. 

greatz Matthieu

---

### Post by Matthieu_van_Kints on 2016-09-26
just want to add that the issue continues and that it is not just a simple error from a newby but does seem to be a genuine bug some how.

any reply would be highly appreciated. 

also posted it on ask ubuntu: [http://askubuntu.com/questions/828267/2e-display-disappeared-after-reboot](http://askubuntu.com/questions/828267/2e-display-disappeared-after-reboot)

without reply.

---

