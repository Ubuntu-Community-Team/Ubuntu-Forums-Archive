---
title: "Kernel 5.4.0-9-generic"
date: 2020-01-08
forum: Hardware
---

### Post by MyMurry on 2020-01-08
Hello!

I have sound problems with this new kernel and my nvidia card (hdmi). Could this the reason?

[https://devtalk.nvidia.com/default/topic/1068441/upgrading-the-linux-graphics-driver-from-440-36-5-to-440-44-2-has-caused-extremely-noisy-audio-via-the-hdmi-port-on-my-gtx-660-ti-graphics-card/](https://devtalk.nvidia.com/default/topic/1068441/upgrading-the-linux-graphics-driver-from-440-36-5-to-440-44-2-has-caused-extremely-noisy-audio-via-the-hdmi-port-on-my-gtx-660-ti-graphics-card/)

Have anyone else this problem?

Regards

---

### Post by SeijiSensei on 2020-01-08
Did you install the NVIDIA driver using the Driver Manager in Ubuntu?

---

### Post by MyMurry on 2020-01-08
via apt, its a server install, the graphics works, only sound isn't working properly.

nvidia-dkms-440
nvidia-driver-440
nvidia-kernel-common-440
nvidia-kernel-source-440
nvidia-utils-440
xserver-xorg-video-nvidia-440 

Kernel 5.3.0-24 is working

---

### Post by slickymaster on 2020-01-09
Thread moved to **Hardware** for a better fit

---

### Post by MyMurry on 2020-01-10
Hello!

Fixed with 5.4.0-11-generic

---

