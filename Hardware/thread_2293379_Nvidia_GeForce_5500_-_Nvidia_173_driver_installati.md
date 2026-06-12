---
title: "Nvidia GeForce 5500 - Nvidia 173 driver installation support request"
date: 2015-09-04
forum: Hardware
---

### Post by frizi on 2015-09-04
While using an older - legacy graphic card on our older Computer, my goal is to install the recommended Graphical driver for the Nvidia GeForce 5500 card. The recommended version by Nvidia is the 173.14.39 one.

I've switched to non X Window mode and turned off lightdm so as blacklisted : 
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current
blacklist nvidia-173-updates
blacklist nvidia-96-updates
alias nvidia nvidia_current_updates
alias nouveau off
alias lbm-nouveau off

Also installed: sudo apt-get install build-essential linux-headers-generic dkms 
and extended GRUB with the nomodset setting.

At installation of the driver, the first issue is reported as: "The distribution-provided pre-install script failed! Continue installation anyway?"
then: "ERROR: Unable to build NVIDIA kernel module."
and finally: "ERROR: Installation has failed. Please see the file '/var/log/nvidia-installer.log' for details. You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com."

My further attempt was by adding certain PPA and trying to install it by apt-get but the versoin 173 was not available. There are many threads regarding this issue for older Ubuntu versions. Any idea how to make the Nvidia GeForce 5500 Graphic card running on 15.04?

Thank you in advance!

---

### Post by Yellow Pasque on 2015-09-04
> Any idea how to make the Nvidia GeForce 5500 Graphic card running on 15.04?

The 173.xx proprietary driver is not going to work on Ubuntu 15.04. The Xserver is too new and Nvidia is not releasing any new versions of the 173 series.
The latest version of Ubuntu that will support the 173.xx driver is Ubuntu 14.04**.1**

---

### Post by frizi on 2015-09-04
Thank you Temüjin. Since many ears I am using Linux and Ubuntu because of the older HW support. It is hard to believe that suddenly I will have to use old Software versions that are not updatable.
Is there really no way to make this running?

---

### Post by Yellow Pasque on 2015-09-04
What's wrong with the open-source nouveau driver that is installed by default?

---

### Post by frizi on 2015-09-05
I was trying to optimize as much as possible the performance since when watching videos in large and full screen mode they was not playing fluent. Therefor I thought that the graphic driver has to be updated. I will try with the recommended version on Ubuntu 14.04.01. Thank you for your advice.

---

### Post by deadflowr on 2015-09-05
for what it's worth you can get the 14.04.1 version here
[http://old-releases.ubuntu.com/releases/14.04.0/](http://old-releases.ubuntu.com/releases/14.04.0/)
Don't mind that it says old-releases.
It will still get full support until 2019.

And after you fully update it should say it's at 14.04.3
but it'll still be using the 14.04.1 kernel series and graphics stack.
Which is what is important.

Hope it helps

---

### Post by frizi on 2015-09-05
Thank you deadflowr. I will start straight with the version 14.04.01 as recommended by Temüjin. Let's see if it will work.

---

### Post by mörgæs on 2015-09-05
Does it have to be the 173 series or will a younger class of Nvidia drivers do?

---

### Post by Yellow Pasque on 2015-09-05
> **mörgæs said:**
> Does it have to be the 173 series or will a younger class of Nvidia drivers do?

It has to be 173 series because it's the last to support Geforce 5/FX cards.

---

### Post by mörgæs on 2015-09-06
Thanks for info. 
I posted because am running Nvidia 304 on GeForce 6150- and 6800 cards with good results so I was wondering if they also worked for 5xxx.

---

### Post by Yellow Pasque on 2015-09-06
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by frizi on 2015-09-06
As recommended, I had installed the Ubuntu version 14.04.01, installed the Nvidia 173 driver and mentioned a significant performance improvement. After that, the dist-upgrade increased the system version to 14.04.03. For that old Computer the right setup needed.
Great, I am very happy for the achievement and for the great reply received here. Thanks.

---

