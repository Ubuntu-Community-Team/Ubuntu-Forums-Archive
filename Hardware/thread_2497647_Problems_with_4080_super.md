---
title: "Problems with 4080 super"
date: 2024-05-13
forum: Hardware
---

### Post by giantflyingegg on 2024-05-13
I dual boot windows and 24.04. The gpu works fine in windows. I have tried multiple times to install various nvidia drivers, either through additional drivers and then also via command line. Nvidia-smi says No devices found. Many hours of trouble shooting with chatgpt and ive got nowhere. Any suggestions?

Edit: things i have tried

1) fresh install of 24.04 then installing 550 driver via additional drivers
2) fresh install and installing 550 via command line
3) install from ppa
4) ssh and disable display manager before install via command line
5) blacklist nouveau
6) disable secure boot
7) installed steam to verify that steam could not identify the gpu (only igpu detected)
8) installing 24.04 with igpu disabled
9) installing 24.04 with igpu disabled and nomodeset

---

### Post by Autodave on 2024-05-13
What kernel are you using?  You need to be on 6.5  And use the 535 driver from the repository.

---

### Post by giantflyingegg on 2024-05-13
6.8. The nvidia site says the 4080 super is only supported by driver 550

---

### Post by Yellow Pasque on 2024-05-13
Get more information. Attach the resulting nvidia-bug-report.log.gz file.
```
sudo nvidia-bug-report.sh
```

---

### Post by Autodave on 2024-05-13
I read the nVidia site as saying that the 550 is the newest....not the only option.

---

### Post by Yellow Pasque on 2024-05-13
> **Autodave said:**
> I read the nVidia site as saying that the 550 is the newest....not the only option.

The "Super" cards need 550.  Please give a link to what you read. Here are the supported products from the release notes of the latest versions of the two drivers:

> 535.179
GeForce RTX 40 Series:
NVIDIA GeForce RTX 4090 D, NVIDIA GeForce RTX 4090, NVIDIA GeForce RTX 4080, NVIDIA GeForce RTX 4070 Ti, NVIDIA GeForce RTX 4070, NVIDIA GeForce RTX 4060 Ti, NVIDIA GeForce RTX 4060

> 550.78
GeForce RTX 40 Series:
NVIDIA GeForce RTX 4090 D, NVIDIA GeForce RTX 4090, NVIDIA GeForce RTX 4080 SUPER, NVIDIA GeForce RTX 4080, NVIDIA GeForce RTX 4070 Ti SUPER, NVIDIA GeForce RTX 4070 Ti, NVIDIA GeForce RTX 4070 SUPER, NVIDIA GeForce RTX 4070, NVIDIA GeForce RTX 4060 Ti, NVIDIA GeForce RTX 4060

If you want to see the listing of PCI ID's
[http://us.download.nvidia.com/XFree86/Linux-x86_64/535.179/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/535.179/README/supportedchips.html)
[http://us.download.nvidia.com/XFree86/Linux-x86_64/550.78/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/550.78/README/supportedchips.html)


Also, why would you tell someone running 24.04 to use a 6.5 kernel? That doesn't make any sense.

---

### Post by giantflyingegg on 2024-05-14
Heres the bug report following a fresh install and adding the driver via additional drivers

---

### Post by giantflyingegg on 2024-05-14
Solved. After all that i just had to update the bios

---

### Post by Yellow Pasque on 2024-05-14
Yeah, I would have looked at BIOS memory address settings (Above 4G Decoding, Re-Sizable BAR, etc.) But I'm glad the update straightened it out. Please mark the thread SOLVED (Thread Tools menu above first post).

```
2024-05-14T12:05:40.454048+01:00 gfe-System-Product-Name kernel: nvidia-nvlink: Nvlink Core is being initialized, major device number 511
2024-05-14T12:05:40.454049+01:00 gfe-System-Product-Name kernel: NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
2024-05-14T12:05:40.454049+01:00 gfe-System-Product-Name kernel: NVRM: BAR1 is 0M @ 0x0 (PCI:0000:01:00.0)
2024-05-14T12:05:40.454049+01:00 gfe-System-Product-Name kernel: NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
2024-05-14T12:05:40.454049+01:00 gfe-System-Product-Name kernel: NVRM: BAR2 is 0M @ 0x0 (PCI:0000:01:00.0)
2024-05-14T12:05:40.454049+01:00 gfe-System-Product-Name kernel: NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
2024-05-14T12:05:40.454050+01:00 gfe-System-Product-Name kernel: NVRM: BAR3 is 0M @ 0x0 (PCI:0000:01:00.0)
2024-05-14T12:05:40.454050+01:00 gfe-System-Product-Name kernel: NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
2024-05-14T12:05:40.454050+01:00 gfe-System-Product-Name kernel: NVRM: BAR4 is 0M @ 0x0 (PCI:0000:01:00.0)
2024-05-14T12:05:40.454050+01:00 gfe-System-Product-Name kernel: NVRM: loading NVIDIA UNIX x86_64 Kernel Module  550.67  Tue Mar 12 23:54:15 UTC 2024
2024-05-14T12:05:40.454051+01:00 gfe-System-Product-Name kernel: nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  550.67  Tue Mar 12 23:29:25 UTC 2024
2024-05-14T12:05:40.454053+01:00 gfe-System-Product-Name kernel: [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver
2024-05-14T12:05:41.070397+01:00 gfe-System-Product-Name kernel: NVRM: GPU 0000:01:00.0: RmInitAdapter failed! (0x24:0x72:1556)
2024-05-14T12:05:41.070402+01:00 gfe-System-Product-Name kernel: NVRM: GPU 0000:01:00.0: rm_init_adapter failed, device minor number 0
```

---

