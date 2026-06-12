---
title: "AMD Drivers Ubuntu 12.10"
date: 2013-01-03
forum: Hardware
---

### Post by TStarkH on 2013-01-03
Hi everyone!

Here's my problem:

I have an HP Elitebook 8560p with a Radeon HD 6470M (Not sure, but it's a 6XXX). I installed the Latest drivers from the AMD Support website (12.11 beta version) It works, but it has become very slow. I tried to uninstall them but I got an error:

```
*** AMD Catalyst(TM) Proprietary Driver Uninstall Log 2013-01-03 14:33:57 ***
md5sum integrity check failed for /usr/lib/xorg/modules/drivers/fglrx_drv.so.
One or more files have been altered since installation.
Uninstall will not be completed.

To force uninstall, removing all installed files without verification,
run /usr/share/ati/amd-uninstall.sh --force.

Forcing uninstall is not recommended and may cause system corruption.
```

I'm a bit lost. I tried to purge every fglrx packages but it doesn't work. Output :

```
sudo apt-get --purge remove fglrx**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx**'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx**'
Note, selecting 'fglrx-amdcccle-updates' for regex 'fglrx**'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx**'
Note, selecting 'fglrx' for regex 'fglrx**'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx**'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx**'
Note, selecting 'fglrx-updates' for regex 'fglrx**'
Note, selecting 'glx-alternative-fglrx' for regex 'fglrx**'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx**'
Note, selecting 'fglrx-updates-dev' for regex 'fglrx**'
Note, selecting 'fglrx-dev' for regex 'fglrx**'
Note, selecting 'fglrx-glx' for regex 'fglrx**'
Note, selecting 'fglrx-modaliases' for regex 'fglrx**'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx**'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx**'
Note, selecting 'fglrx-driver' for regex 'fglrx**'
Note, selecting 'fglrx-control' for regex 'fglrx**'
Package 'fglrx-glx' is not installed, so not removed
Package 'fglrx-kernel-source' is not installed, so not removed
Package 'fglrx-modaliases' is not installed, so not removed
Package 'xfree86-driver-fglrx' is not installed, so not removed
Package 'xorg-driver-fglrx' is not installed, so not removed
Package 'fglrx-control-qt2' is not installed, so not removed
Package 'xfree86-driver-fglrx-dev' is not installed, so not removed
Package 'xorg-driver-fglrx-dev' is not installed, so not removed
Package 'fglrx' is not installed, so not removed
Package 'fglrx-amdcccle' is not installed, so not removed
Package 'fglrx-amdcccle-updates' is not installed, so not removed
Package 'fglrx-dev' is not installed, so not removed
Package 'fglrx-updates' is not installed, so not removed
Package 'fglrx-updates-dev' is not installed, so not removed
Package 'glx-alternative-fglrx' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```


Is there a specific recommended version of ATI drivers to install? Or do I have to wait for AMD to release a new version?

---

### Post by ZombieApocalypse on 2013-01-04
You could try to reinstall the drivers from the package you downloaded from the AMD website (you may need to use the --force command) and then retry then uninstall script. The sudo apt-get --purge remove fglrx** command won't work because your not using the drivers from the repositories.

---

### Post by ZombieApocalypse on 2013-01-04
When you installed the 12.11 beta drivers did you take the steps to remove the watermark? If so then I think this is why the uninstall script won't work. You need to re-edit /etc/ati/signature so that it reads "UNSIGNED" again (and deleted the inserted code).

---

### Post by TStarkH on 2013-01-06
Thanks for the help! I finally forced the uninstall script. It didn't break the system and got back to the natives drivers. I found a good configuration. I changed the kernel to 3.7.1 and everything works fine! Thanks again!

---

