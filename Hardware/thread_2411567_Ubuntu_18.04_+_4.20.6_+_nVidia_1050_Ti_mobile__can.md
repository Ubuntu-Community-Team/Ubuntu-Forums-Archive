---
title: "Ubuntu 18.04 + 4.20.6 + nVidia 1050 Ti mobile : can't install drivers"
date: 2019-01-31
forum: Hardware
---

### Post by boxerab on 2019-01-31
I haven't had any luck with latest 415 driver. 
Can anyone advise on how to proceed? Try older kernel or older driver ?
I've tried a few with no luck.
nvidia-smi always fails to connect to driver.

I've disabled secure boot, btw.

---

### Post by Autodave on 2019-01-31
Where are you getting that driver from?  You need to use the one from the repositories: do NOT try to install the driver from the Nvidia site!  Just use the newest one in the repositories. Or, go to Settings -> Additional drivers and use the recommended one.

---

### Post by boxerab on 2019-01-31
Thanks. I was using
sudo ubuntu-drivers autoinstall

---

### Post by Autodave on 2019-01-31
Interesting because the newest driver in the repositories is 3.90.xx.  I have no idea how you would have gotten the 415.xx driver.  Let's try this: go to Settings -> Additional Drivers and see what one is recommended.  Then let it install.  Reboot and see what happens.  Let is know.

---

### Post by boxerab on 2019-01-31
Thanks. I tried, that, but if installs 4.15 . I tried specifying 3.90, but that driver doesn't work either.

---

### Post by boxerab on 2019-01-31
I have a ppa for the latest drivers, btw.

---

### Post by boxerab on 2019-01-31
500 [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64)  Packages
     origin developer.download.nvidia.com

---

