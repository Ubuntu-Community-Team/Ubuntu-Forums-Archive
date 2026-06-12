---
title: "SMBus module is not loaded (Unclaimed) It is a error?"
date: 2011-12-26
forum: Hardware
---

### Post by livre1 on 2011-12-26
The module (driver) SMBus is not being charged as stated below:


00(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage


I have to report this as a bug on Launchpad?

Using Ubuntu 10.04.

---

### Post by wolfen69 on 2011-12-26
Are you having issues using your computer? I have installed windows countless times and left out the smbus controller, but it didn't seem to affect anything. If there are no issues, I wouldn't worry about it.

---

### Post by livre1 on 2011-12-29
I do not notice any problem that I think have to do with the "SMbus".


However, it appears SMbus has certain functions.

This would not be an error?

---

