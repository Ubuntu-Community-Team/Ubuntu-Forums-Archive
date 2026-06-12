---
title: "Reviving a GMA600/Atom tablet"
date: 2020-06-23
forum: Hardware
---

### Post by bhmo2kn on 2020-06-23
Unfortunately the most current GMA500/EMGD thread [https://ubuntuforums.org/showthread.php?t=2107593](https://ubuntuforums.org/showthread.php?t=2107593) is closed, so starting a new one.   I'm trying to revive the Fujitsu STYLISTIC Q550 (Atom Z670, GMA 600) tablet. Had it working with the Ubuntu's included gma500_gfx, but anything over 12.04 is using the software OpenGL, so it's unbearably slow. Tried to install emgd, and it looks that I have all the required packages and configs, but getting:```
(EE) No devices detected. Fatal server error: no screens found
```Quite stuck here atm. All the relevant (hopefully) logs are linked [https://pastebin.com/aqe0rcds](https://pastebin.com/aqe0rcds), also there is an open issue over there [https://github.com/EMGD-Community/intel-binaries-linux/issues/60](https://github.com/EMGD-Community/intel-binaries-linux/issues/60), but it seems that thopiekar is missing atm. Tried all the conf files at [https://github.com/EMGD-Community/intel-binaries-linux/tree/master/config/xorg.conf](https://github.com/EMGD-Community/intel-binaries-linux/tree/master/config/xorg.conf) as a starting point and also that script [http://bazaar.launchpad.net/~gma500/+junk/emgd-xorg-conf/view/head:/src/emgd-xorg-conf.py](http://bazaar.launchpad.net/~gma500/+junk/emgd-xorg-conf/view/head:/src/emgd-xorg-conf.py) with no success. As there where no success trying the 4.4.0-97-lowlatency kernel.  Modprobing the gma500_gfx driver, replacing the driver name in xorg.conf and replacing the libgl1-mesa-glx package with libgl1-mesa-7.9-swx11 brings back the desktop. So it looks that everything else is correct here. Could it be the GMA**6**00 the culprit?

---

