---
title: "AMD APU + GPU OpenCL processing."
date: 2013-03-15
forum: Hardware
---

### Post by voidwalker on 2013-03-15
I have installed Catalyst 13.1 driver and AMD APP SDK 2.80 for OpenCL opencl support. I can only use the GPU right now.

Let me do a ```
sudo amdconfig --initial --adapter=all
```
, remove all other xorg.confs and reboot my machine.
> Number of devices:                 2
  Device Type:                     CL_DEVICE_TYPE_GPU

It's weird since they both show in ```
clinfo
```, also ```
export COMPUTE=:0
``` does not give the result.

This is pretty much how far I have gotten with Googling around.

---

### Post by voidwalker on 2013-04-06
Since the last X mess I ended up removing all proprietary drivers stated above, use open drivers to boot and then install 2:9.000-0ubuntu3 from Ubuntu repos. It didn't change much. It's using the integrated APU GPU, I can't change those settings from  the CCC or thru amdconfig --adapter. If I manually mess with Xorg.conf  files my whole X goes down.

---

