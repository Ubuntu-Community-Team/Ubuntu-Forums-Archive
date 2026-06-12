---
title: "cannot make Blender use opencl of my integrated AMD GPU"
date: 2022-03-04
forum: Hardware
---

### Post by sim-snorlax on 2022-03-04
I followed this: [https://amdgpu-install.readthedocs.io/en/latest/install-script.html](https://amdgpu-install.readthedocs.io/en/latest/install-script.html), and installed ```
--opencl=legacy
``` (I installed rocr but then I couldn't use clinfo command, it just returned Segmentfault......)

```

$ clinfo
Number of platforms                               1
  Platform Name                                   AMD Accelerated Parallel Processing
  Platform Vendor                                 Advanced Micro Devices, Inc.
  Platform Version                                OpenCL 2.1 AMD-APP (3380.4)
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_icd cl_amd_event_callback cl_amd_offline_devices 
  Platform Host timer resolution                  1ns
  Platform Extensions function suffix             AMD

  Platform Name                                   AMD Accelerated Parallel Processing
Number of devices                                 0

NULL platform behavior
  clGetPlatformInfo(NULL, CL_PLATFORM_NAME, ...)  No platform
  clGetDeviceIDs(NULL, CL_DEVICE_TYPE_ALL, ...)   No platform
  clCreateContext(NULL, ...) [default]            No platform
  clCreateContext(NULL, ...) [other]              No platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_DEFAULT)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CPU)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_GPU)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ACCELERATOR)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CUSTOM)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ALL)  No devices found in platform

```

```

$ neofetch
            .-/+oossssoo+/-.               sim@simputer 
        `:+ssssssssssssssssss+:`           ------------ 
      -+ssssssssssssssssssyyssss+-         OS: Ubuntu 20.04.4 LTS x86_64 
    .ossssssssssssssssssdMMMNysssso.       Host: Code 01 Series PF5NU1G Standard 
   /ssssssssssshdmmNNmmyNMMMMhssssss/      Kernel: 5.13.0-30-generic 
  +ssssssssshmydMMMMMMMNddddyssssssss+     Uptime: 38 mins 
 /sssssssshNMMMyhhyyyyhmNMMMNhssssssss/    Packages: 1884 (dpkg), 10 (snap) 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Shell: bash 5.0.17 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   Resolution: 1920x1080, 1920x1080 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   WM: i3 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   Theme: Adwaita [GTK3] 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   Icons: Adwaita [GTK3] 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Terminal: gnome-terminal 
 /sssssssshNMMMyhhyyyyhdNMMMNhssssssss/    CPU: AMD Ryzen 7 4800H with Radeon Graphics (16) @ 2.900GHz 
  +sssssssssdmydMMMMMMMMddddyssssssss+     GPU: AMD ATI 04:00.0 Renoir 
   /ssssssssssshdmNNNNmyNMMMMhssssss/      Memory: 4352MiB / 38022MiB 
    .ossssssssssssssssssdMMMNysssso.
      -+sssssssssssssssssyyyssss+-                                 
        `:+ssssssssssssssssss+:`                                   
            .-/+oossssoo+/-.



```
Just switched from debian to resolve the issue, it seems I still have the opencl issue on Ubuntu 20.04 while they claimed to support it!

---

### Post by dougdeep2 on 2022-03-08
By any chance, did you check to see which driver the kernel is trying to use?
```

lspci -k | grep -EA3 'VGA|3D|Display'

```
should return something like
```

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland PRO [Radeon R7 240/340]
    Subsystem: Hightech Information System Ltd. Oland PRO [Radeon R7 240/340]
    Kernel driver in use: amdgpu
    Kernel modules: radeon, amdgpu

```
or, in your case, it will return the name of your GPU.  When my GPU was misbehaving, the "Kernel driver is use:" was radeon and not amdgpu.  Apparently the radeon driver is a fallback in case amdgpu fails to load.  If that is happening with your machine you may need to look at dmesg.  It's a long file written at startup but it may show where amdgpu is failing.  Maybe something like:
```

[    6.165565] kernel: amdgpu 0000:01:00.0: Direct firmware load for amdgpu/oland_uvd.bin failed with error -2
[    6.165573] kernel: amdgpu 0000:01:00.0: amdgpu: amdgpu_uvd: Can't load firmware "amdgpu/oland_uvd.bin"
[    6.165579] kernel: [drm:amdgpu_device_ip_init [amdgpu]] *ERROR* sw_init of IP block <uvd_v3_1> failed -2
[    6.165977] kernel: amdgpu 0000:01:00.0: amdgpu: amdgpu_device_ip_init failed
[    6.165980] kernel: amdgpu 0000:01:00.0: amdgpu: Fatal error during GPU init
[    6.165985] kernel: amdgpu 0000:01:00.0: amdgpu: amdgpu: finishing device.

```

---

### Post by QIII on 2022-03-08
There was absolutely no reason to install a driver.  In fact, you may have cobbled things up.

When Ubuntu is installed, it will either load and use the amdgpu module or the radeon module depending on which supports the particular AMD GPU.  For you, that would be amdgpu.

Let's be sure the module is loaded and running.  Please post the results of


```
lsmod | grep amdgpu
```

amdgpu is a Linux kernel module, so it's not a question of whether Ubuntu supports it.  Canonical doesn't write the module and they don't modify it in their kernel.  Canonical and AMD have had a long love affair.

---

