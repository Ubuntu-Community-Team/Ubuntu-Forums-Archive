---
title: "[Ubuntu 16.04.2 LTS]Dell Latitude E7450 + Docking Station"
date: 2017-02-28
forum: Hardware
---

### Post by jabbajac on 2017-02-28
Hi! 

I have a Dell Latitude E7450 running Ubuntu 16.04.2 LTS with Gnome 3. I'm having a few issues with the docking station where it undocks perfectly fine, and everything shows up correctly but upon docking only the monitor will work. All USB devices seem to not work until I reboot on the dock. Also I have an occasional hiccup where my  monitor will cut out. The monitor is connected via a displayport on the dock. I've upgraded my kernel as that seems to have solved the problem for some other people but it did not work for me. Any help would be much appreciated...also if there's any other commands I could run for debugging, I'd love to know what they are. 

Thank you!

```

~%: uname -a
Linux u847beb14625d58acde3f 4.8.0-34-generic #36~16.04.1-Ubuntu SMP Wed Dec 21 18:55:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
~%: cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
NAME="Ubuntu"
VERSION="16.04.2 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.2 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial

```

---

