---
title: "Linux: Browsers has no hardware acceleration Nvidia 840M"
date: 2021-05-12
forum: Hardware
---

### Post by laukokpin on 2021-05-12
My laptop has a nvidia 840m geforce card. I'm trying to get hardware acceleration working for youtube on the browser.


As the cpu heats up. 


After spending much time going through forums and guides. I found out that vdpau is not even enabled.


THe result of vdpauinfo. and vaainfo is bellow.


vdpauinfo
display: :1   screen: 0
GPU at BusId 0x1 doesn't have a supported video decoder
Error creating VDPAU device: 1




vainfo
libva info: VA-API version 1.8.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so
libva info: Found init function __vaDriverInit_1_7
GPU at BusId 0x1 doesn't have a supported video decoder
libva error: /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so init failed
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit




Ubuntu 20.10

---

### Post by ajgreeny on 2021-05-12
Which browser, and what version?

---

### Post by Yellow Pasque on 2021-05-13
What laptop? Does it have an intel integrated GPU? I'm guessing it does.
You should use the Intel GPU for video decoding and general use. Save the Nvidia GPU for gaming.

---

