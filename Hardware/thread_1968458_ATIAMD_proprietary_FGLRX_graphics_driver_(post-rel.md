---
title: "ATI/AMD proprietary FGLRX graphics driver (post-release updates)"
date: 2012-04-29
forum: Hardware
---

### Post by karypid on 2012-04-29
I have an HP EliteBook 8460p with a discrete ATI Graphics card. According to the manufacturer's web page ([http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-3740645-3955549-5056942.html?dnr=1](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-3740645-3955549-5056942.html?dnr=1))  it is an AMD Radeon HD 6470M. The card works fine, with the default  install, but I want to activate the proprietary driver to get 3D  performance for some games. The additional drivers module provides me  with two options:

1) ATI/AMD proprietary FGLRX graphics driver
2) ATI/AMD proprietary FGLRX graphics driver (post-release updates)

Although (1) installs successfully, when I try to install (2) I get a  generic "installation failed" message and instructed to check the  /var/log/jockey.log file (attached).

After the failed installation, I do see the packages installed as follows:

```
dpkg -l | grep fglrx
ii  fglrx-amdcccle-updates                 2:8.960-0ubuntu1                         Catalyst Control Center for the AMD graphics accelerators
ii  fglrx-updates                          2:8.960-0ubuntu1                         Video driver for the AMD graphics accelerators
```After the  reboot, the my X.org log (attached) mentions:

```
...
[     5.017] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[     5.017] (II) ATI Proprietary Linux Driver Release Identifier: 8.96.7                               
[     5.017] (II) ATI Proprietary Linux Driver Build Date: Mar 12 2012 13:06:50
[     5.017] (II) RADEON: Driver for ATI Radeon chipsets:
        ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
        ATI Radeon Mobility X300 (M24) 3152 (PCIE),
        ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
...
```

...and also:

```
karypid@harmony:/var/log$ lsmod | grep fglrx
fglrx                3263886  108 
```

So what is it that has failed? The driver seems to be installed and loaded, so... why the error message?

---

### Post by MonkeyPaw on 2012-04-29
If you go over the support.amd.com and download their Linux Catalyst drivers, you should have success. I'm guessing that the "Additional Drivers" version of the drivers is older and doesn't like your hardware.

---

### Post by 1204 on 2012-04-29
This is good step-by-step help to AMD drivers. It has also spesific troubleshooting if anything goes wrong. [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by Yellow Pasque on 2012-04-29
fglrx-updates seems to be screwed up right now. [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/949641](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/949641)

See comment #10 on that bug for workaround that lets you install regular fglrx package (which is using the same version of Catalyst as fglrx-updates since Precise was just released).

> /var/log/jockey.log file (attached).
I don't see it...

---

