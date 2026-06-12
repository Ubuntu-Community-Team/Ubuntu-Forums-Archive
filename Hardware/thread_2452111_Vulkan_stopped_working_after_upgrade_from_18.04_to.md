---
title: "Vulkan stopped working after upgrade from 18.04 to 20.04"
date: 2020-10-16
forum: Hardware
---

### Post by Fun Miles on 2020-10-16
I've upgraded my linux box from 18.04 to 20.04. Since then, I am unable to run any Vulkan programs. Any Vulkan programs that runs cannot find a present queue.
I have two NVidia Quadro P1000 and am running the NVidia 455 drivers and I've  installed NVidia's CUDA drivers.

Running vkcube gives:
> Could not find both graphics and present queues
  
and the output of vulkaninfo can be found at  [https://pastebin.com/hPa79te4](https://pastebin.com/hPa79te4)

---

### Post by Fun Miles on 2020-10-16
I downgraded from NVidia 455 to 450 and now Vulkan works again. But CUDA does not. Running a previously sample CUDA program outputs:
 >  AllocGPUassert: the provided PTX was compiled with an unsupported toolchain. main.cu 29

Any idea how to get both CUDA and Vulkan up an running?

---

### Post by CelticWarrior on 2020-10-16
If you install cuda from the Ubuntu repositories it should work.
And, according to Nvidia, Quadro P1000 is supported by 450, not by 455, anyway. Please check the Nvidia website for the recommended version before doing "experiments". Please note that you shouldn't install the drivers from there, only to check the currently recommended version. Always install the drivers from the Ubuntu repository or the graphics drivers PPA if the official repo (from an old release) doesn't provide said version.

---

### Post by Fun Miles on 2020-10-17
@CelticWarrior I installed 455 from Ubuntu repository.  It was more or less pushed on me by the Ubuntu CUDA driver install. and the output of "ubuntu-drivers devices" lists:
> WARNING:root:_pkg_get_support nvidia-driver-455: package has invalid Support Betaheader, cannot determine support level== /sys/devices/pci0000:72/0000:72:00.0/0000:73:00.0 ==
modalias : pci:v000010DEd00001CB1sv00001028sd000011BCbc03sc00i00
vendor   : NVIDIA Corporation
model    : GP107GL [Quadro P1000]
driver   : nvidia-driver-450 - third-party free
driver   : nvidia-driver-435 - distro non-free
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-455 - third-party free recommended
driver   : nvidia-driver-440-server - distro non-free
driver   : nvidia-driver-418-server - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

So 455 is recommended. I followed some recommendations elsewhere for updating the ubuntu package sources and since that the warning you see appears. It makes it a bit strange that a beta would be recommended. One can also find news that NVidia has a beta for Vulkan 1.2 on 455. But I don't know how to install that.

I removed the nvidia nvcc that worked with the 455 drivers and used   `sudo apt install nvidia-cuda-toolkit` and now CUDA works. Everything is under the 450 drivers.

---

