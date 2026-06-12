---
title: "GeForce 610M with ubuntu 13.10"
date: 2014-03-26
forum: Hardware
---

### Post by antani3 on 2014-03-26
How can I check to have installed correctly the proprietary nvidia driver?
why **glxgears** with and w/o **optirun,** the output it's pretty much the same:
59 FPS.


> lsmod | grep nvidia


gives 0 lines.


But according to `dpkg -l` I have the following packages:


```
    ii  bumblebee-nvidia                                            3.2.1-5~xedgers~saucy1                                amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
    ii  nvidia-331                                                  331.49-0ubuntu1~xedgers13.10.3                        amd64        NVIDIA binary driver - version 331.49
    ii  nvidia-common                                               1:0.2.83                                              amd64        transitional package for ubuntu-drivers-common
    rc  nvidia-libopencl1-304                                       304.119-0ubuntu1~xedgers13.10.1                       amd64        NVIDIA OpenCL Driver and ICD Loader library
    ii  nvidia-libopencl1-331                                       331.49-0ubuntu1~xedgers13.10.3                        amd64        NVIDIA OpenCL Driver and ICD Loader library
    rc  nvidia-opencl-icd-304                                       304.119-0ubuntu1~xedgers13.10.1                       amd64        NVIDIA OpenCL ICD
    ii  nvidia-opencl-icd-331                                       331.49-0ubuntu1~xedgers13.10.3                        amd64        NVIDIA OpenCL ICD
    ii  nvidia-settings                                             331.38-0ubuntu1~xedgers~saucy1                        amd64        Tool for configuring the NVIDIA graphics driver

```

Also:
`optirun glxheads` gives:


>   GL_VENDOR:   NVIDIA Corporation   
>   GL_RENDERER: GeForce 610M/PCIe/SSE2


while `glxheads` alone:


>   GL_VENDOR:   Intel Open Source Technology Center   
>   GL_RENDERER: Mesa DRI Intel(R) Ivybridge Mobile

---

