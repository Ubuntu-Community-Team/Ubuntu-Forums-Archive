---
title: "How to restrict CUDA to a specific GPU"
date: 2016-04-01
forum: Hardware
---

### Post by bwanaaa on 2016-04-01
Two NVIDIA 780Ti cards installed. Using cuda 7.5 on Ubuntu 14.04. Postinstallation checklist shows cuda installed properly and functions properly. My monitors are attached to device 0. I compiled the cuda samples and ran nvidia-smi. ITs output shows two NVIDIA cards as expected:

```
Fri Apr  1 01:04:31 2016       
+------------------------------------------------------+                       
| NVIDIA-SMI 352.79     Driver Version: 352.79         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 780 Ti  Off  | 0000:01:00.0     N/A |                  N/A |
| 38%   50C    P2    N/A /  N/A |   1084MiB /  3071MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
|   1  GeForce GTX 780 Ti  Off  | 0000:03:00.0     N/A |                  N/A |
| 29%   34C    P8    N/A /  N/A |     11MiB /  3071MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0                  Not Supported                                         |
|    1                  Not Supported                                         |
+-----------------------------------------------------------------------------+
```
However deviceQuery only shows 1 card:

```
./deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

Detected 1 CUDA Capable device(s)

Device 0: "GeForce GTX 780 Ti"
  CUDA Driver Version / Runtime Version          7.5 / 7.5
  CUDA Capability Major/Minor version number:    3.5
  Total amount of global memory:                 3072 MBytes (3221028864 bytes)
  (15) Multiprocessors, (192) CUDA Cores/MP:     2880 CUDA Cores
  GPU Max Clock rate:                            1084 MHz (1.08 GHz)
  Memory Clock rate:                             3500 Mhz
  Memory Bus Width:                              384-bit
  L2 Cache Size:                                 1572864 bytes
  Maximum Texture Dimension Size (x,y,z)         1D=(65536), 2D=(65536, 65536), 3D=(4096, 4096, 4096)
  Maximum Layered 1D Texture Size, (num) layers  1D=(16384), 2048 layers
  Maximum Layered 2D Texture Size, (num) layers  2D=(16384, 16384), 2048 layers
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       49152 bytes
  Total number of registers available per block: 65536
  Warp size:                                     32
  Maximum number of threads per multiprocessor:  2048
  Maximum number of threads per block:           1024
  Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
  Max dimension size of a grid size    (x,y,z): (2147483647, 65535, 65535)
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             512 bytes
  Concurrent copy and kernel execution:          Yes with 1 copy engine(s)
  Run time limit on kernels:                     No
  Integrated GPU sharing Host Memory:            No
  Support host page-locked memory mapping:       Yes
  Alignment requirement for Surfaces:            Yes
  Device has ECC support:                        Disabled
  Device supports Unified Addressing (UVA):      Yes
  Device PCI Domain ID / Bus ID / location ID:   0 / 3 / 0
  Compute Mode:
     < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 7.5, CUDA Runtime Version = 7.5, NumDevs = 1, Device0 = GeForce GTX 780 Ti
Result = PASS
```
I tried to direct cuda to the other video card using the environment variable

CUDA_VISIBLE_DEVICES=1

I added the line

 ```
export CUDA_VISIBLE_DEVICES=1 
```
to .bashrc and opened a new terminal window. Printenv showed me CUDA_VISIBLE_DEVICES=1 among others.

I ran bandwidthTest. Its output is:

```
[CUDA Bandwidth Test] - Starting...
Running on...

 Device 0: GeForce GTX 780 Ti
 Quick Mode

 Host to Device Bandwidth, 1 Device(s)
 PINNED Memory Transfers
   Transfer Size (Bytes)    Bandwidth(MB/s)
   33554432         11618.3

 Device to Host Bandwidth, 1 Device(s)
 PINNED Memory Transfers
   Transfer Size (Bytes)    Bandwidth(MB/s)
   33554432         12909.9

 Device to Device Bandwidth, 1 Device(s)
 PINNED Memory Transfers
   Transfer Size (Bytes)    Bandwidth(MB/s)
   33554432         265048.1

Result = PASS
```
I rebooted and reran bandwidthTest but it still starts its output with:

```
[CUDA Bandwidth Test] - Starting...
    Running on...

     Device 0: GeForce GTX 780 Ti
     Quick Mode
..... 
```
bandwidthTest is STILL using Device 0. I want it to use device 1. Why did deviceQuery only see one card? What am I missing?

---

