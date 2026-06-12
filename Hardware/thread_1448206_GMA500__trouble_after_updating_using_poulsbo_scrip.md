---
title: "GMA500 : trouble after updating using poulsbo script"
date: 2010-04-06
forum: Hardware
---

### Post by limaunion on 2010-04-06
Hi all! today I updated my dell inspiron mini and for some reason the video driver stopped to work as expected. I'm getting the following errors:

Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to solve this.

(EE) PSB(0): the stolenBase is:0x3f8000000
(EE) PSB(0): screnIndex is:0;fbPhys is:0x3f9000000; fbsize is:0x007df000
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(EE) [drm]: drmOpen failed. Disabling DRI.
(EE) [drm] Could not uninstall irq handler.
(EE) PSB(0): This driver currently needs DRM to operate.

When I installed Karmic a couple of months ago I ran the poulsbo.sh script as described here [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#karmic](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#karmic)

Now for some reason it's not working with the new kernel (2.6.31-20-generic), there're some errors like:

Loading new psb-kernel-source-4.41.6 DKMS files...
Error! Could not find module source directory.
Directory: /usr/src/psb-kernel-source-4.41.6 does not exist.

I've all the files (11) related to this script under /tmp.

Any idea on how to solve this problem?
TIA!
LU

PS: I tried to rollback to 2.6.31-14-generic and re-run the script but got the same results.

---

### Post by mikewhatever on 2010-04-06
You need to run *[SIZE="3"]sudo dpkg-reconfigure psb-kernel-source[/SIZE]* after every kernel update. If that doesn't work, try reinstalling the *psb-kernel-source* package.

---

### Post by limaunion on 2010-04-06
> **mikewhatever said:**
> You need to run *[SIZE="3"]sudo dpkg-reconfigure psb-kernel-source[/SIZE]* after every kernel update. If that doesn't work, try reinstalling the *psb-kernel-source* package.

OK, thanks so much, I finally managed to solve this by running dpkg -i /tmp/psb-kernel-source.

Best regards
LU

---

### Post by mikewhatever on 2010-04-06
Great! Now, you can make dkms take care of it for future kernel updates.
(dkms - Dynamic Kernel Module Support)

All you need to do is add **AUTOINSTALL="yes"** to the following two config files:

/usr/src/psb-kernel-source-4.41.6/dkms.conf

/var/lib/dkms/psb-kernel-source/4.41.6/build/dkms.conf

---

