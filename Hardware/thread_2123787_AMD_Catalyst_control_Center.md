---
title: "AMD Catalyst control Center"
date: 2013-03-08
forum: Hardware
---

### Post by Dazedndconfused on 2013-03-08
I want to start off by saying that I am on Ubuntu 12.10. Also I am not a very experienced linux user.

when i try to install the catalyst control center it tells me that i dont have all the proper tools installed. Here is what it tells me.

Supported adapter detected.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-25-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.

Can someone tell me what the tools required for installation are?

---

### Post by jonnyboysmithy on 2013-03-09
You need to have the linux headers kernels installed.
Install them using:```

sudo apt-get install linux-headers-$(uname -r)
```

Source:
[http://superuser.com/questions/475736/missing-linux-headers-during-ati-driver-installation](http://superuser.com/questions/475736/missing-linux-headers-during-ati-driver-installation)

---

