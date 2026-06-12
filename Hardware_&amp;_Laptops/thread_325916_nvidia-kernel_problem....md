---
title: "nvidia-kernel problem..."
date: 2006-12-26
forum: Hardware &amp; Laptops
---

### Post by ubuntu-mike022465 on 2006-12-26
Folks, I'm kind of stumped right now, I've tried to enable the nvidia driver within xorg.conf by changing it from "nv" to "nvidia", and tried to restart X, but I get this error:

API mismatch: the client has the version 1.0-8776, but this kernel module has the version 1.0-8762.  Please make sure that this kernel module and all NVIDIA driver components have the same version.

The restricted drivers are from the repositories, as well as they are the most current for Dapper.  Is there anything I can do to enable hardware acceleration, or can someone point me to the repositories that have the appropriate nvidia-kernel for the x server module?

Thanks

M.

---

### Post by spockrock on 2006-12-26
did you install the restricted modules with the .run installer from the nvidia site??

---

### Post by ubuntu-mike022465 on 2006-12-26
No. Just what was in the repositories.

M.

---

### Post by spockrock on 2006-12-27
did you recently update or anything of that nature??

---

### Post by ubuntu-mike022465 on 2006-12-27
I'm constantly trying to stay on top of the updates as they become available.  I'm not at my laptop right now, but I seem to recall as part of the error message when trying to start up X with the nvidia driver, that the X server module was built using the 1.0.8762 driver, and that nvidia-kernel module uses the 1.0.8776 version.  Not sure what more information I can give, unless there's suggestions that will allow me to post something a little more accurate than my memory... :-k  :mrgreen: 

M.

BTW, I've checked xorg.0.log and there's bugger all in there to help diagnose the problem.  Maybe I'm just checking in the wrong place. :-| 

M.

---

### Post by spockrock on 2006-12-27
you did install nvidia-glx right??

Also do you have the restricted modules installed as well??

---

### Post by ubuntu-mike022465 on 2006-12-27
Yes and yes.

M.

---

### Post by ubuntu-mike022465 on 2006-12-31
Has anyone else been having difficulty with getting their nvidia driver working with the latest packages from the repositories?

M.

---

### Post by Ted.Verhagen on 2007-01-13
Had the same problem. 

I had the NVIDIA driver installed from the Ubuntu repository, however after installation things didn't work the way I expected them to work (something went wrong with the configuration of the Xorg.conf file). So I decided to download the NVIDIA drivers from the NVIDIA site and install them manually. ([http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html))

After rebooting the machine I got:

API mismatch: the client has the version 1.0-9746, but this kernel module has the version 1.0-8762. Please make sure that this kernel module and all NVIDIA driver components have the same version.

Uninstalling the NVIDIA driver which I had installed from the Ubuntu repository did the trick (I did re-install the driver from the NVIDIA site afterwards just to be sure).

Just checkout which kernel module (nvidia.ko) is installed "/lib/modules/`uname -r`/kernel/drivers/video" directory

---

### Post by valkarin on 2007-01-13
I also had the same problem.  After I got rid of the drivers and reset xorg.conf, I used synaptic to get the nvidia-glx and the kernel modules listed in [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") on the ubuntu wiki.  Has worked pretty well since.  Got 3D anyway.

---

