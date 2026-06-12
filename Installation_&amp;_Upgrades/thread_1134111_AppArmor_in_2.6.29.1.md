---
title: "AppArmor in 2.6.29.1"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Silvr2008 on 2009-04-23
So I just compiled the 2.6.29.1 kernel and when I reboot I see that the AppArmor module failed to start. When I try to invoke it says that the AppArmor module is not loaded.

I tried to download the source from [https://launchpad.net/ubuntu/intrepid/+source/apparmor/2.3+1289-0ubuntu4](https://launchpad.net/ubuntu/intrepid/+source/apparmor/2.3+1289-0ubuntu4) but when I do the make it says:

error: Unable to open .spec: No such file or directory
error: Name field must be present in package: (main package)
error: Version field must be present in package: (main package)
error: Release field must be present in package: (main package)
error: Summary field must be present in package: (main package)
error: Group field must be present in package: (main package)
error: License field must be present in package: (main package)
error: query of specfile .spec failed, can't parse
cvs tag IMMUNIX-
make: cvs: Command not found
make: *** [cvs_tag] Error 127

Anyone got it to work, or have any suggestions for me?

---

