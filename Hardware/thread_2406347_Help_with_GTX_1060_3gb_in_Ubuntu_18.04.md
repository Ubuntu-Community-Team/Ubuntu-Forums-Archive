---
title: "Help with GTX 1060 3gb in Ubuntu 18.04"
date: 2018-11-19
forum: Hardware
---

### Post by mstrozier on 2018-11-19
Good afternoon.  I have installed a EVGA GTX 1060 3gb card in my linux box, I have the current nvidia drivers 410.73 installed and all seems to be working except that I have some concerns on the power draw.  It's showing 394 watts / 120 watts when I use nvidia-smi.   When I do the power check it shows draw also at 394 watts.  This concerns me.  See below as I didn't see this when I had my 1050ti in before it.

Mon Nov 19 13:20:49 2018       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 410.73       Driver Version: 410.73       CUDA Version: 10.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 106...  Off  | 00000000:01:00.0  On |                  N/A |
| 57%   29C    P5   394W / 120W |    273MiB /  3018MiB |      4%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0      1140      G   /usr/lib/xorg/Xorg                            18MiB |
|    0      1174      G   /usr/bin/gnome-shell                          49MiB |
|    0      1344      G   /usr/lib/xorg/Xorg                            94MiB |
|    0      1478      G   /usr/bin/gnome-shell                         107MiB |
|    0      1822      G   /usr/bin/nvidia-settings                       0MiB |
+-----------------------------------------------------------------------------+




And here is the power listing

==============NVSMI LOG==============

Timestamp                           : Mon Nov 19 13:27:03 2018
Driver Version                      : 410.73
CUDA Version                        : 10.0

Attached GPUs                       : 1
GPU 00000000:01:00.0
    Power Readings
        Power Management            : Supported
        Power Draw                  : 393.40 W
        Power Limit                 : 120.00 W
        Default Power Limit         : 120.00 W
        Enforced Power Limit        : 120.00 W
        Min Power Limit             : 60.00 W
        Max Power Limit             : 140.00 W
    Power Samples
        Duration                    : 12.29 sec
        Number of Samples           : 119
        Max                         : 394.46 W
        Min                         : 392.17 W
        Avg                         : 393.88 W



any help with this would be appreciated.   Thanks

---

