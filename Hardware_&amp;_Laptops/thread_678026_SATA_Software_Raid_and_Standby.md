---
title: "SATA Software Raid and Standby"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by raijinsetsu on 2008-01-25
I have two sata drives set-up in a raid-0 array. I want to conserve some power in this system, so I want them to go into standby. The system is always on, but the array is not always in use. However, some application in the system is accessing the hard-drives before they complete their spin-down (this is dangerous), so they never actually power down.
The array only stores my media files, and is mounted on /usr/local/media. Normal system daemons should not access this frequently.

So, my question is: what can I use to track which applications are accessing the drive?

Any comments or suggestions are welcome.

---

### Post by opscure on 2008-01-25
You could try using fuser to determine what processes are impacting your device.  ie:```
fuser -m -u /dev/yourdevice
```

---

### Post by raijinsetsu on 2008-01-28
Thanks. That's quite actually helpful :)

---

