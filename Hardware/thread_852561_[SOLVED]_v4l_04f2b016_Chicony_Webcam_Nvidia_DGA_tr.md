---
title: "[SOLVED] v4l 04f2:b016 Chicony Webcam Nvidia DGA trouble"
date: 2008-07-07
forum: Hardware
---

### Post by starcannon on 2008-07-07
I'm having an Nvidia DGA problem on Ubuntu 32bit... Nvidia does not use dga, so how does one configure v4l ?

heres my v4l-conf output
```

starcannon@starcannon-laptop:~$ v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13

```

Here's my xawtv output:
```

~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-19-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0xb6b7add0b7de0450 [PAL_I,PAL_D1,PAL_Nc,SECAM_D,SECAM_G,SECAM_H,SECAM_K,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
v4l2: oops: select timeout

```

Can anyone point me in the right direction on how to solve this? I've been googling my fingers off, I guess I'm not asking it the right questions. I can gather and post any additional information that would be of use, just let me know how I can help you help me :)

Heres my video Card, it works flawlessly.
```

~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: GeForce 8400M GS
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

Heres the webcam I'm ultimately trying to configure:
```

~$ lsusb
Bus 004 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd 

```

Thanks for looking,
~starcannon

---

### Post by starcannon on 2008-09-10
September 10, 2008

The latest drivers from:
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

using these directions:
[http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC](http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC)

and then these directions:
[http://openfacts.berlios.de/index-en.phtml?title=HowTo_compile_for_Ubuntu_6.06_LTS](http://openfacts.berlios.de/index-en.phtml?title=HowTo_compile_for_Ubuntu_6.06_LTS)

The camera now works flawlessly in cheese and skype.

I'll write up an all in one place guide here on the forums, I'm tired right now though, so will just leave everyone with these links for now.

---

### Post by starcannon on 2008-11-12
This camera works out of the box in 8.10 Intrepid Ibex.

---

