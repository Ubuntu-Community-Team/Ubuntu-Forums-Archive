---
title: "External Monitor display"
date: 2014-05-24
forum: Hardware
---

### Post by Palash_Mittal on 2014-05-24
I have Ubuntu 14.04 LTS and Windows 8.1 installed on my Dell XPS L502X with Nvidia Graphic Card GF108M(GeForce GT 540M). My external monitor works fine in Windows but it is not getting detected in Ubuntu. What are the possible reasons for that and how to fix it?

---

### Post by dannyboy79 on 2014-05-24
how is it connected? what graphics driver are you using for your GT 540M?

---

### Post by Palash_Mittal on 2014-05-24
dpkg -l | grep nvidia
returns this
```
rc  nvidia-304-updates                                          304.117-0ubuntu1                                    amd64        NVIDIA legacy binary driver - version 304.117
rc  nvidia-331                                                  331.38-0ubuntu7                                     amd64        NVIDIA binary driver - version 331.38
rc  nvidia-libopencl1-304-updates                               304.117-0ubuntu1                                    amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-libopencl1-331                                       331.38-0ubuntu7                                     amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-opencl-icd-304-updates                               304.117-0ubuntu1                                    amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-331                                       331.38-0ubuntu7                                     amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                             331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-updates                                     331.20-0ubuntu8                                     amd64        Transitional package for nvidia-settings

```

I wrote that inorder to confirm that HDMI port is working correctly, and to rule the probablity of hardware problems.

---

### Post by dannyboy79 on 2014-05-24
due to you having an intel igpu and an nvidia card you may need to investigate optimus. you also failed to tell us how it's connected, HDMI, DVI, VGA or what?

---

### Post by Palash_Mittal on 2014-05-25
its connected via HDMI port.

---

### Post by Palash_Mittal on 2014-05-29
Can anybody help? Its first time I am asking on this forum so I am not sure what information I have to provide.

---

### Post by dannyboy79 on 2014-05-29
apparently there's a long standing bug, [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1040053](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1040053)

---

