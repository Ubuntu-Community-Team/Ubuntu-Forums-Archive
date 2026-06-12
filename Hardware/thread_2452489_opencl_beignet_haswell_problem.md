---
title: "opencl beignet haswell problem"
date: 2020-10-23
forum: Hardware
---

### Post by stevelcb on 2020-10-23
```
kubuntu 20.04

5.4.0-52-generic
```

Hi everyone
I'm trying to run the StarTools GPU accelerated version, but I'm getting errors. The program becomes unusable afterwards.
Here is my clinfo:


```
Number of platforms                               1
  Platform Name                                   Intel Gen OCL Driver
  Platform Vendor                                 Intel
  Platform Version                                OpenCL 2.0 beignet 1.3
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_global_int32_base_atomics cl_khr
_global_int32_extended_atomics cl_khr_local_int32_base_atomics cl_khr_local_int32_extende
d_atomics cl_khr_byte_addressable_store cl_khr_3d_image_writes cl_khr_image2d_from_buffer
 cl_khr_depth_images cl_khr_spir cl_khr_icd cl_intel_accelerator cl_intel_subgroups cl_in
tel_subgroups_short
  Platform Extensions function suffix             Intel

  Platform Name                                   Intel Gen OCL Driver
Number of devices                                 1
  Device Name                                     Intel(R) HD Graphics Haswell Ultrabook 
GT2 reserved
  Device Vendor                                   Intel
  Device Vendor ID                                0x8086
  Device Version                                  OpenCL 1.2 beignet 1.3
  Driver Version                                  1.3
  Device OpenCL C Version                         OpenCL C 1.2 beignet 1.3
  Device Type                                     GPU
  Device Profile                                  FULL_PROFILE
  Device Available                                Yes
  Compiler Available                              Yes
  Linker Available                                Yes
  Max compute units                               20
  Max clock frequency                             1000MHz
  Device Partition                                (core)
    Max number of sub-devices                     1
    Supported partition types                     None, None, None
    Supported affinity domains                    (n/a)
  Max work item dimensions                        3
  Max work item sizes                             512x512x512
  Max work group size                             512
  Preferred work group size multiple              16
  Preferred / native vector sizes                  
    char                                                16 / 8        
    short                                                8 / 8        
    int                                                  4 / 4        
    long                                                 2 / 2        
    half                                                 0 / 8        (n/a)
    float                                                4 / 4        
    double                                               0 / 2        (n/a)
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
  Global memory size                              2147483648 (2GiB)
  Error Correction support                        No
  Max memory allocation                           1610612736 (1.5GiB)
  Unified memory for Host and Device              Yes
  Minimum alignment for any data type             128 bytes
  Alignment of base address                       1024 bits (128 bytes)
  Global Memory cache type                        Read/Write
  Global Memory cache size                        8192 (8KiB)
  Global Memory cache line size                   64 bytes
  Image support                                   Yes
    Max number of samplers per kernel             16
    Max size for 1D images from buffer            65536 pixels
    Max 1D or 2D image array size                 2048 images
    Base address alignment for 2D image buffers   4096 bytes
    Pitch alignment for 2D image buffers          1 pixels
    Max 2D image size                             8192x8192 pixels
    Max 3D image size                             8192x8192x2048 pixels
    Max number of read image args                 128
    Max number of write image args                8
  Local memory type                               Local
  Local memory size                               65536 (64KiB)
  Max number of constant args                     8
  Max constant buffer size                        134217728 (128MiB)
  Max size of kernel argument                     1024
  Queue properties                                 
    Out-of-order execution                        No
    Profiling                                     Yes
  Prefer user sync for interop                    Yes
  Profiling timer resolution                      80ns
  Execution capabilities                           
    Run OpenCL kernels                            Yes
    Run native kernels                            Yes
    SPIR versions                                 1.2
  printf() buffer size                            1048576 (1024KiB)
  Built-in kernels                                __cl_copy_region_align4;__cl_copy_regio
n_align16;__cl_cpy_region_unalign_same_offset;__cl_copy_region_unalign_dst_offset;__cl_co
py_region_unalign_src_offset;__cl_copy_buffer_rect;__cl_copy_image_1d_to_1d;__cl_copy_ima
ge_2d_to_2d;__cl_copy_image_3d_to_2d;__cl_copy_image_2d_to_3d;__cl_copy_image_3d_to_3d;__
cl_copy_image_2d_to_buffer;__cl_copy_image_3d_to_buffer;__cl_copy_buffer_to_image_2d;__cl
_copy_buffer_to_image_3d;__cl_fill_region_unalign;__cl_fill_region_align2;__cl_fill_regio
n_align4;__cl_fill_region_align8_2;__cl_fill_region_align8_4;__cl_fill_region_align8_8;__
cl_fill_region_align8_16;__cl_fill_region_align128;__cl_fill_image_1d;__cl_fill_image_1d_
array;__cl_fill_image_2d;__cl_fill_image_2d_array;__cl_fill_image_3d;
  Device Extensions                               cl_khr_global_int32_base_atomics cl_khr
_global_int32_extended_atomics cl_khr_local_int32_base_atomics cl_khr_local_int32_extende
d_atomics cl_khr_byte_addressable_store cl_khr_3d_image_writes cl_khr_image2d_from_buffer
 cl_khr_depth_images cl_khr_spir cl_khr_icd cl_intel_accelerator cl_intel_subgroups cl_in
tel_subgroups_short

NULL platform behavior
  clGetPlatformInfo(NULL, CL_PLATFORM_NAME, ...)  Intel Gen OCL Driver
  clGetDeviceIDs(NULL, CL_DEVICE_TYPE_ALL, ...)   Success [Intel]
  clCreateContext(NULL, ...) [default]            Success [Intel]
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_DEFAULT)  Success (1)
    Platform Name                                 Intel Gen OCL Driver
    Device Name                                   Intel(R) HD Graphics Haswell Ultrabook 
GT2 reserved
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CPU)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_GPU)  Success (1)
    Platform Name                                 Intel Gen OCL Driver
    Device Name                                   Intel(R) HD Graphics Haswell Ultrabook 
GT2 reserved
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ACCELERATOR)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CUSTOM)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ALL)  Success (1)
    Platform Name                                 Intel Gen OCL Driver
    Device Name                                   Intel(R) HD Graphics Haswell Ultrabook 
GT2 reserved

ICD loader properties
  ICD loader Name                                 OpenCL ICD Loader
  ICD loader Vendor                               OCL Icd free software
  ICD loader Version                              2.2.11
  ICD loader Profile                              OpenCL 2.1
```

And here are the first 5 (of hundreds) of errors from beignet:

```
./StarTools-Linux64-GPU
drm_intel_gem_bo_context_exec() failed: Input/output error
Beignet: "Exec event 0x7f5c9001e610 error, type is 4592, error status is -5"
drm_intel_gem_bo_context_exec() failed: Input/output error
Beignet: "Exec event 0x7f5c9002b0e0 error, type is 4592, error status is -5"
drm_intel_gem_bo_context_exec() failed: Input/output error
Beignet: "Exec event 0x7f5c9001dc10 error, type is 4592, error status is -5"
drm_intel_gem_bo_context_exec() failed: Input/output error
Beignet: "Exec event 0x7f5c9001de00 error, type is 4592, error status is -5"
drm_intel_gem_bo_context_exec() failed: Input/output error
Beignet: "Exec event 0x7f5c9002bfd0 error, type is 4592, error status is -5"
drm_intel_gem_bo_context_exec() failed: Input/output error
```

Any ideas anyone?
Cheers and TIA,
Steve

---

### Post by slickymaster on 2020-10-23
*Thread moved to **Hardware**.*

---

