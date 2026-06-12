---
title: "amd-driver-installer-15.201.2401-x86.x86_64.run --NoXServer on Ubuntu 20.10 groovy"
date: 2020-12-19
forum: Hardware
---

### Post by ychemin on 2020-12-19
**amd-driver-installer-15.201.2401-x86.x86_64.run --NoXServer on Ubuntu 20.10 groovy runs forever**

Ubuntu 20.10 updated today, on a Celeron J1900 4 cores 1.99GHz

Graphic card is FirePro v5800

downloaded driver at:
[https://www.amd.com/en/support/professional-graphics/legacy-products/firepro-v-series/firepro-v5800](https://www.amd.com/en/support/professional-graphics/legacy-products/firepro-v-series/firepro-v5800)


~/fglrx-15.201.2401$ sudo ./amd-driver-installer-15.201.2401-x86.x86_64.run --buildpkg Ubuntu/groovy --NoXServer
Created directory fglrx-install.lsnkom
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-15.201.2401......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/groovy
Building X independent packages


Duplicate to ask support at AMD: [https://community.amd.com/t5/drivers-software/amd-driver-installer-15-201-2401-x86-x86-64-run-noxserver-on/m-p/431876#M135835](https://community.amd.com/t5/drivers-software/amd-driver-installer-15-201-2401-x86-x86-64-run-noxserver-on/m-p/431876#M135835)

---

### Post by CelticWarrior on 2020-12-19
Welcome.

Ubuntu already has open-source drivers for AMD and old ATI cards.
There's no need to install any other drivers and actually you can't use that old drivers because it's incompatible with modern kernel versions. The driver automatically installed should work and it's not like you'll get any better performance with that relic anyway.

---

### Post by ajgreeny on 2020-12-19
That's not the way to install AMD graphic drivers in Ubuntu, and the OS should generally in the most recent versions install the required driver at installation by default, either **Radeon** driver or **amdpro** depending on graphic card. You would not need to do anything.

I have not used AMD hardware for a very long time now so I'm not sure which driver is needed, though as that card is fairly old I think it will be radeon that's needed.  Did you have a graphics problem before trying to install the driver manually?

---

### Post by QIII on 2020-12-19
fglrx is dead and has been for some time now. AMD no longer maintains it for Linux and modern Linux distributions no longer work with it.  If you do manage to get it to install, you will be quite lucky if you can still use your machine.

---

### Post by ychemin on 2020-12-20
OK, thank you for all your responses. I am trying to make OpenCL work on that old card for scientific computations only, not for display. Do you mean that it "works out of the box"?

---

### Post by QIII on 2020-12-20
Would you please post the results of 

```
lsmod | grep radeon
```

and

```
lsmod | grep amdgpu
```

We'll be able to see from those whether the amdgpu or radeon module is loaded.

Given the age of that card -- before GCN (Graphics Core Next) -- I doubt is is supported by amdgpu.

---

### Post by ychemin on 2020-12-20
Only lsmod | grep radeon returns something:

```
lsmod | grep radeon
radeon               1503232  1
ttm                   102400  1 radeon
i2c_algo_bit           16384  2 radeon,i915
drm_kms_helper        225280  2 radeon,i915
drm                   565248  11 drm_kms_helper,radeon,i915,ttm
```

---

### Post by ychemin on 2020-12-20
hmmm... interesting, now OpenCL is also happy.


```
clinfo
Number of platforms                               1
  Platform Name                                   Clover
  Platform Vendor                                 Mesa
  Platform Version                                OpenCL 1.1 Mesa 21.0.0-devel (git-f9ceab7 2020-12-20 groovy-oibaf-ppa)
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_icd
  Platform Extensions function suffix             MESA

  Platform Name                                   Clover
Number of devices                                 1
  Device Name                                     AMD JUNIPER (DRM 2.50.0 / 5.8.0-33-generic, LLVM 11.0.0)
  Device Vendor                                   AMD
  Device Vendor ID                                0x1002
  Device Version                                  OpenCL 1.1 Mesa 21.0.0-devel (git-f9ceab7 2020-12-20 groovy-oibaf-ppa)
  Driver Version                                  21.0.0-devel
  Device OpenCL C Version                         OpenCL C 1.1 
  Device Type                                     GPU
  Device Profile                                  FULL_PROFILE
  Device Available                                Yes
  Compiler Available                              Yes
  Max compute units                               10
  Max clock frequency                             690MHz
  Max work item dimensions                        3
  Max work item sizes                             256x256x256
  Max work group size                             256
  Preferred work group size multiple              64
  Preferred / native vector sizes                 
    char                                                16 / 16      
    short                                                8 / 8       
    int                                                  4 / 4       
    long                                                 2 / 2       
    half                                                 0 / 0        (n/a)
    float                                                4 / 4       
    double                                               0 / 0        (n/a)
  Half-precision Floating-point support           (n/a)
  Single-precision Floating-point support         (core)
    Denormals                                     No
    Infinity and NANs                             Yes
    Round to nearest                              Yes
    Round to zero                                 No
    Round to infinity                             No
    IEEE754-2008 fused multiply-add               No
    Support is emulated in software               No
    Correctly-rounded divide and sqrt operations  No
  Double-precision Floating-point support         (n/a)
  Address bits                                    32, Little-Endian
  Global memory size                              1073741824 (1024MiB)
  Error Correction support                        No
  Max memory allocation                           751619276 (716.8MiB)
  Unified memory for Host and Device              No
  Minimum alignment for any data type             128 bytes
  Alignment of base address                       32768 bits (4096 bytes)
  Global Memory cache type                        None
  Image support                                   No
  Local memory type                               Local
  Local memory size                               32768 (32KiB)
  Max number of constant args                     15
  Max constant buffer size                        751619276 (716.8MiB)
  Max size of kernel argument                     1024
  Queue properties                                
    Out-of-order execution                        No
    Profiling                                     Yes
  Profiling timer resolution                      0ns
  Execution capabilities                          
    Run OpenCL kernels                            Yes
    Run native kernels                            No
  Device Extensions                               cl_khr_byte_addressable_store cl_khr_global_int32_base_atomics cl_khr_global_int32_extended_atomics cl_khr_local_int32_base_atomics cl_khr_local_int32_extended_atomics

NULL platform behavior
  clGetPlatformInfo(NULL, CL_PLATFORM_NAME, ...)  No platform
  clGetDeviceIDs(NULL, CL_DEVICE_TYPE_ALL, ...)   No platform
  clCreateContext(NULL, ...) [default]            No platform
  clCreateContext(NULL, ...) [other]              Success [MESA]
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_DEFAULT)  No platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CPU)  No platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_GPU)  No platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ACCELERATOR)  No platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CUSTOM)  No platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ALL)  No platform
```

---

