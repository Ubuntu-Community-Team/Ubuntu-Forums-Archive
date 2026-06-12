---
title: "Cups won't start, HP X6180 won't scan"
date: 2010-07-29
forum: Hardware
---

### Post by jgo2la on 2010-07-29
On my Ubuntu 10.04 install, cups doesn't start at bootup for some reason. However, if I manually run:
```
/etc/init.d/cups start
```
then my printers show up and everything works as it should. I checked the rc.d links already, and they're as they should be. What could be causing this?

Additionally, in the process of figuring out the above cups issue, I installed hplip separately from the package manager, then removed it, and then installed the version from the package manager (thinking that hplip was the cause of the lack of printing ability before I discovered that it was actually cups's issue). Now my networked HP Photosmart C6180 can print as before, but Simple Scan and XSane fail to find it; before this mess, they were able to find it and scan from it just fine. How can I fix this?

---

