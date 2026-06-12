---
title: "Tesla P100 Installation problem"
date: 2023-08-06
forum: Hardware
---

### Post by cemdede on 2023-08-06
Hi,

I cannot make this one work:
I have **Dell R730**, which works on **Ubuntu 22.04.3**.LTS
I used **Riser 3** and added a **P100**.
I enabled BIOS GPU Legacy settings - then disabled
[COLOR=#333333]I already enabled" **Memory Mapped I/O above 4 GB**” on BIOS settings.[/COLOR]
[COLOR=#333333]I disabled “**Embedded Video Controlle**r” on BIOS settings[/COLOR]
[COLOR=#333333]The card is plugged into **slot 6 on Riser 3 with 8 pin cable** ([/COLOR][For DELL R730 8pin to 8pin Power Cable Nvidia K80/M40/M60/P40/P100 PCIE GPU @USA | eBay]("https://www.ebay.com/itm/274624139602")[COLOR=#333333]).[/COLOR]
 
I used NVIDIA cuda developer website to download the driver and used:
sudo sh cuda_12.2.1_535.86.10_linux.run --no-opengl-libs

in order to prevent from installing OPENGL libraries

nvcc -V

nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2021 NVIDIA Corporation
Built on Thu_Nov_18_09:45:30_PST_2021
Cuda compilation tools, release 11.5, V11.5.119
Build cuda_11.5.r11.5/compiler.30672275_0

[B]In the end:
[/B]
lsmod | grep nvidia


nvidia_drm             77824  0
nvidia_modeset       1302528  1 nvidia_drm
nvidia              56532992  1 nvidia_modeset
nvidiafb               61440  0
vgastate               24576  1 nvidiafb
fb_ddc                 16384  1 nvidiafb
i2c_algo_bit           16384  2 nvidiafb,mgag200
drm_kms_helper        311296  4 mgag200,nvidia_drm
drm                   622592  5 drm_kms_helper,nvidia,mgag200,nvidia_drm

lspci | grep NVIDIA
03:00.0 3D controller: NVIDIA Corporation GP100GL [Tesla P100 PCIe 16GB] (rev a1)

nvidia-smi
No devices were found


**I tried different ways to install the driver but when I ask for nvidia-smi I always get No devices found.**
**Could you please help?**


sudo dmesg | grep nvidia


[   11.925467] nvidiafb: Device ID: 10de15f8 
[   11.925473] nvidiafb: unknown NV_ARCH
[   12.015811] nvidia: loading out-of-tree module taints kernel.
[   12.015827] nvidia: module license 'NVIDIA' taints kernel.
[   12.074954] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[   12.097370] nvidia-nvlink: Nvlink Core is being initialized, major device number 508
[   12.236719] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  535.86.10  Wed Jul 26 23:01:50 UTC 2023
[   12.242512] [drm] [nvidia-drm] [GPU ID 0x00000300] Loading driver
[   12.242514] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:03:00.0 on minor 1
[   12.409378] audit: type=1400 audit(1691342857.950:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=1573 comm="apparmor_parser"
[   12.409403] audit: type=1400 audit(1691342857.950:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=1573 comm="apparmor_parser"
[  531.056647] [drm] [nvidia-drm] [GPU ID 0x00000300] Unloading driver
[  531.106298] nvidia-modeset: Unloading
[  531.139051] nvidia-nvlink: Unregistered Nvlink Core, major device number 508
[  546.540595] nvidia-nvlink: Nvlink Core is being initialized, major device number 508
[  546.693604] nvidia_uvm: module uses symbols from proprietary module nvidia, inheriting taint.
[  546.699398] nvidia-uvm: Loaded the UVM driver, major device number 506.
[  546.705225] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  535.86.10  Wed Jul 26 23:01:50 UTC 2023
[  546.708939] [drm] [nvidia-drm] [GPU ID 0x00000300] Loading driver
[  546.708942] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:03:00.0 on minor 1
[  546.714750] [drm] [nvidia-drm] [GPU ID 0x00000300] Unloading driver
[  546.752891] nvidia-modeset: Unloading
[  546.780644] nvidia-uvm: Unloaded the UVM driver.
[  546.809003] nvidia-nvlink: Unregistered Nvlink Core, major device number 508
[  562.200098] nvidia-nvlink: Nvlink Core is being initialized, major device number 508
[  562.322454] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  535.86.10  Wed Jul 26 23:01:50 UTC 2023
[  562.325817] [drm] [nvidia-drm] [GPU ID 0x00000300] Loading driver
[  562.325819] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:03:00.0 on minor 1
[  747.837871] nvidia_uvm: module uses symbols from proprietary module nvidia, inheriting taint.
[  747.844925] nvidia-uvm: Loaded the UVM driver, major device number 506.
```


* nvidia: module verification failed - indicates signed driver issue
* nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver
* nvidia-uvm: Loaded the UVM driver


So the core nvidia driver and UVM/modeset modules are loading.
The signature verification failed warning can likely be ignored for now.


**Why nvidia-smi still doesn't detect the GPU if the modules are clearly loading????? Does anyone has any clue???**

[COLOR=#333333][FONT=&amp]
**For people who will later face the same problems:**
**FAN SPEED**
**Enable manual fan control:**
sudo ipmitool raw 0x30 0x30 0x01 0x00
**For example, to set the fan speed to 20%:**
sudo ipmitool raw 0x30 0x30 0x02 0xff 0x14
**Monitor fan speed:**
sudo ipmitool sdr type fan
**Monitor temperature:**
sudo ipmitool sdr type temperature


[/FONT][/COLOR]

---

### Post by guiverc on 2023-08-06
I see mention of Ubuntu 22.04.3, but no product details (ie. Server, Desktop, *flavor* etc) as those influence which kernel stack is default, which makes significant difference with kernel modules.

The Ubuntu 22.04.3 LTS media is still in testing (*though in RC status thus should be good*), but you didn't specify what actual media you used; with 3 kernel stacks available currently for 22.04 media (2 for 22.04.3).

---

### Post by cemdede on 2023-08-07
NVIDIA Thank you for pointing that out, guiverc. Here are the speccification of my server machine:
[B]
Dell PowerEdge R730, 2x 2699V3, 288GB DDR4Ram, 2x1100W
GPU: NVIDIA Tesla P100 PCIe 16GB (Riser 3 -Slot6)
OS: Ubuntu 22.04.3 LTS x86_64 Server
Kernel: 5.15.0-78-generic
Shell: bash 5.1.16

[/B][COLOR=#1C1917][FONT=-apple-system]uname -r[/FONT][/COLOR]
[COLOR=#1C1917][FONT=-apple-system]5.15.0-78-generic

[/FONT][/COLOR]
[COLOR=#1C1917][FONT=-apple-system]modinfo nvidia | grep vermagic[/FONT][/COLOR]
[COLOR=#1C1917][FONT=-apple-system]vermagic:       5.15.0-78-generic SMP mod_unload modversions[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-08-07
Please post commands and output of, within [noparse]```

```[/noparse] Tags... That is a Forums Policy. You might want to go back and edit your last post.

You showed what the software was doing (dmesg), but not how Linux see's your hardware... Please post the output of 
```

sudo lspci 
sudo lshw -c video -businfo

```

And according to Dell Publication "Dell EMC PowerEdge Servers with NVIDIA GPUs and VMware vSphere".: [https://dl.dell.com/manuals/all-products/esuprt_server_int/esuprt_server_int_poweredge/esuprt_server_rack/poweredge-r730_concept-guide5_en-us.pdf](https://dl.dell.com/manuals/all-products/esuprt_server_int/esuprt_server_int_poweredge/esuprt_server_rack/poweredge-r730_concept-guide5_en-us.pdf)
```

5. On the PowerEdge R740 server, after installing the vGPU VIB in ESXi, the command nvidia-smi fails
to display the GPU statistics with following error message:
Failed to initialize NVML: Unknown Error
- Resolution:
The above error can occur for many reasons, including misconfiguration. To resolve the issue:
1. Ensure that the VGPU VIB installed successfully without any errors.
2. Verify that the NVIDIA GPUs in the ESXi host are not configured as pass-through devices for VM
DirectPath IO or vDGA.
3. Run the command lspci | grep -i nvida on ESXi shell and ensure that there are entries
related to NVIDIA GPUs present in the server.
4. On Dell EMC PowerEdge yx4x servers, ensure the below settings in System BIOS are set:
• Memory Mapped I/O above 4 GB is set to Enable
• Memory Mapped I/O Base is set to 512 GB

```
Sorry, I am still certified as an Onsite Warranty Tech for Dell, HP, and Lenovo, even though I still do not work as... I still have access to the service doc's.

---

