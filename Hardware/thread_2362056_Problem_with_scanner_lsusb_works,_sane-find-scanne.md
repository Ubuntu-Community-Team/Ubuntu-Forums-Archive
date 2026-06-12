---
title: "Problem with scanner: lsusb works, sane-find-scanner not"
date: 2017-05-23
forum: Hardware
---

### Post by WimiBuntu on 2017-05-23
Dear all

I have Ubuntu 16.04 LTS and a Canon CanoScan Lide 110 flatbed scanner. Previously, I used gscan2pdf and everything worked great. Now, it cannot find the scanner anymore.

I checked, but the SANE Homepage says that model is fully supported using the genesys backend. I also included the rolfbensch repository.

lsusb states
```
Bus 002 Device 008: ID 04a9:1909 Canon, Inc. CanoScan LiDE 110
```

but sudo sane-find-scanner only finds another device
```

found USB scanner (vendor=0x147e [UPEK], product=0x2016 [Biometric Coprocessor]) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```

I have no idea, how to handle this.

Best regards

---

### Post by pdc on 2017-05-23
so it was working on this 16.0 ........ ? ............ for how long?

there are a couple of threads about where scanners are no longer seen; permissions issues .......

---

### Post by WimiBuntu on 2017-05-24
Dear pdc

I am not sure if this will be working in the future, but it kinda get solved. I changed a setting in BIOS for charging USB devices in hibernation mode. And while I am usually not scanning in hibernation mode, the software found the scanner afterwards. If it keeps running, I will not update this thread. If the problem reoccurs, I will send an update.

---

