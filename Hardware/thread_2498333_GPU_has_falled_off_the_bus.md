---
title: "GPU has falled off the bus"
date: 2024-06-09
forum: Hardware
---

### Post by currentshaft on 2024-06-09
bus

---

### Post by Autodave on 2024-06-10
Do you know what GPU is in there?  What, if any, drivers did you install for the GPU and where did you get them from?  What kernel are you running?

---

### Post by currentshaft on 2024-06-12
dsd

---

### Post by #&amp;thj^% on 2024-06-12
If it's not a server the drivers help immensely
```
sudo dmesg -T | grep NVRM
[Wed Jun 12 07:58:43 2024] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  555.52.04  Tue Jun  4 13:54:58 UTC 2024

```
And with the "coolbits" added to your driver install, enables fan control and various power levels.
ie:
```
nvidia-xconfig -a --cool-bits=<your-value-here> --allow-empty-initial-configuration
```

EDIT: Also please have read: [https://wiki.archlinux.org/title/NVIDIA/Tips_and_tricks](https://wiki.archlinux.org/title/NVIDIA/Tips_and_tricks)
```
nvidia-smi -q -d TEMPERATURE

==============NVSMI LOG==============

Timestamp                                 : Wed Jun 12 11:29:39 2024
Driver Version                            : 555.52.04
CUDA Version                              : 12.5

Attached GPUs                             : 1
GPU 00000000:01:00.0
    Temperature
        GPU Current Temp                  : 35 C
        GPU T.Limit Temp                  : N/A
        GPU Shutdown Temp                 : 100 C
        GPU Slowdown Temp                 : 97 C
        GPU Max Operating Temp            : 105 C
        GPU Target Temperature            : 87 C
        Memory Current Temp               : N/A
        Memory Max Operating Temp         : N/A

```

---

