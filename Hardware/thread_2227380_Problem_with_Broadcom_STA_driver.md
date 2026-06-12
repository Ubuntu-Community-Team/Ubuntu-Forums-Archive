---
title: "Problem with Broadcom STA driver"
date: 2014-06-01
forum: Hardware
---

### Post by Jorge_Pimienta on 2014-06-01
Hi everyone.
I have a dell inspiron N7010 with a broadcom BCM4312 and had a lot of problems with the drivers of it, even with the STA in the additional drivers of ubuntu. Just try a lot of possible solutions for my problem and the only one that work for me was:

1) Download the source code of the STA driver from this link:     [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

2)Follow this instructions to build and activate the driver:  [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

When running the command [COLOR=#000000]**modprobe lib80211** or **modprobe ****ieee80211**[/COLOR]**[COLOR=#000000]_crypt_tkip [/COLOR]**[COLOR=#000000]or [/COLOR][COLOR=#000000]**modprobe cfg80211** and then the command [/COLOR]**[COLOR=#000000]insmod wl.ko [/COLOR]**[COLOR=#000000]run it as root using sudo before each command.[/COLOR]

3) Finally after the two following commands: 
[COLOR=#000000]**cp wl.ko /lib/modules/<the kernel version already in use>/kernel/drivers/net/wireless**
[B]depmod -a
[/B][/COLOR][COLOR=#000000]
Set the modules **wl** and the one of the followings [/COLOR][COLOR=#000000]**lib80211** or **ieee80211**[/COLOR]**[COLOR=#000000]_crypt_tkip [/COLOR]**[COLOR=#000000]or [/COLOR][COLOR=#000000]**cfg80211 **that is in execution to load at boot. How to do it is explain in this link: [/COLOR]https://help.ubuntu.com/community/Loadable_Modules
[COLOR=#000000]
Hope this helps
[/COLOR][COLOR=#000000]
[/COLOR]

---

