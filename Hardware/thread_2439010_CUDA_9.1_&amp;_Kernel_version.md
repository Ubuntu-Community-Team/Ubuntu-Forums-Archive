---
title: "CUDA 9.1 &amp; Kernel version"
date: 2020-03-21
forum: Hardware
---

### Post by u666sa on 2020-03-21
What's up.  Please someone explain to me this.

If my video card is GeForce GT 420M, and if 420m only supports CUDA version 9.1, and if cuda9.1[ install guide]("https://docs.nvidia.com/cuda/archive/9.1/cuda-installation-guide-linux/index.html") specifies Linux kernel 4.9.0, does that mean that my installed kernel 5.3.0-42-generic is too new for cuda 9.1 to properly function?  

I'm asking this because if I do john --test=0 --format=opencl I get an error

```
alex@mb2:~/opt/john/run$ ./john --test=0 --format=openclDevice 1: GeForce GT 420M
Testing: sha1crypt-opencl, (NetBSD) [PBKDF1-SHA1 OpenCL]... PASS
Testing: KeePass-opencl [SHA256 AES/Twofish/ChaCha OpenCL]... Options used: -I /home/alex/opt/john/run/opencl -cl-mad-enable -DSM_MAJOR=2 -DSM_MINOR=1 -D__GPU__ -DDEVICE_INFO=16402 -D__SIZEOF_HOST_SIZE_T__=8 -DDEV_VER_MAJOR=390 -DDEV_VER_MINOR=132 -D_OPENCL_COMPILER -DPLAINTEXT_LENGTH=124 -DHASH_LOOPS=100 -DMAX_CONT_SIZE=16777216 ./opencl/keepass_kernel.cl
Build log: In file included from <kernel>:10:
/home/alex/opt/john/run/opencl/opencl_chacha.h:91:18: error: invalid argument type 'const __attribute__((address_space(16776963))) uchar *' (aka 'const __attribute__((address_space(16776963))) unsigned char *') to unary expression
                x->input[12] = !counter ? 0 : U8TO32_LITTLE(counter + 0);
                               ^~~~~~~~
/home/alex/opt/john/run/opencl/opencl_chacha.h:92:18: error: invalid argument type 'const __attribute__((address_space(16776963))) uchar *' (aka 'const __attribute__((address_space(16776963))) unsigned char *') to unary expression
                x->input[13] = !counter ? 0 : U8TO32_LITTLE(counter + 4);
                               ^~~~~~~~
/home/alex/opt/john/run/opencl/opencl_chacha.h:96:18: error: invalid argument type 'const __attribute__((address_space(16776963))) uchar *' (aka 'const __attribute__((address_space(16776963))) unsigned char *') to unary expression
                x->input[12] = !counter ? 0 : U8TO32_LITTLE(counter + 0);
                               ^~~~~~~~
In file included from <kernel>:11:
/home/alex/opt/john/run/opencl/opencl_twofish.h:582:6: error: invalid argument type '__attribute__((address_space(16776963))) Byte *' (aka '__attribute__((address_space(16776963))) unsigned char *') to unary expression
        if (!pInput || (nInputOctets <= 0) || !pOutBuffer)
            ^~~~~~~
/home/alex/opt/john/run/opencl/opencl_twofish.h:582:40: error: invalid argument type '__attribute__((address_space(16776963))) Byte *' (aka '__attribute__((address_space(16776963))) unsigned char *') to unary expression
        if (!pInput || (nInputOctets <= 0) || !pOutBuffer)
                                              ^~~~~~~~~~~
/home/alex/opt/john/run/opencl/opencl_twofish.h:646:6: error: invalid argument type '__attribute__((address_space(16776963))) Byte *' (aka '__attribute__((address_space(16776963))) unsigned char *') to unary expression
        if (!pInput || (nInputOctets <= 0) || !pOutBuffer)
            ^~~~~~~
/home/alex/opt/john/run/opencl/opencl_twofish.h:646:40: error: invalid argument type '__attribute__((address_space(16776963))) Byte *' (aka '__attribute__((address_space(16776963))) unsigned char *') to unary expression
        if (!pInput || (nInputOctets <= 0) || !pOutBuffer)
                                              ^~~~~~~~~~~


Error building kernel ./opencl/keepass_kernel.cl. DEVICE_INFO=16402
0: OpenCL CL_BUILD_PROGRAM_FAILURE (-11) error in opencl_common.c:1376 - clBuildProgram
alex@mb2:~/opt/john/run$ 



```


On the other hand, OpenCL works in Pyrit, but CUDA does not.

```
alex@mb2:~/.pyrit$ pyrit list_coresPyrit 0.5.1 (C) 2008-2011 Lukas Lueg - 2015 John Mora
https://github.com/JPaulMora/Pyrit
This code is distributed under the GNU General Public License v3+


Traceback (most recent call last):
  File "/usr/local/bin/pyrit", line 6, in <module>
    pyrit_cli.Pyrit_CLI().initFromArgv()
  File "/usr/local/lib/python2.7/dist-packages/pyrit_cli.py", line 117, in initFromArgv
    func(self, **options)
  File "/usr/local/lib/python2.7/dist-packages/pyrit_cli.py", line 294, in list_cores
    with cpyrit.cpyrit.CPyrit() as cp:
  File "/usr/local/lib/python2.7/dist-packages/cpyrit/cpyrit.py", line 442, in __init__
    self.CUDAs.append(CUDACore(queue=self, dev_idx=dev_idx))
  File "/usr/local/lib/python2.7/dist-packages/cpyrit/cpyrit.py", line 243, in __init__
    _cpyrit_cuda.CUDADevice.__init__(self, dev_idx)
SystemError: Unknown CUresult.
alex@mb2:~/.pyrit$ 
```

:popcorn::popcorn:](*,)

---

### Post by u666sa on 2020-03-23
Never mind this post.  Because CUDA 9.1 is not supported by GeForce 420M.

You boys need a highly visible guide.... perhaps even Canonical needs anew feature.  On selecting proper cuda version and installing it.

---

### Post by him610 on 2020-03-24
Extract from [https://developer.nvidia.com/cuda-gpus]("https://developer.nvidia.com/cuda-gpus")
```

GPU	                Compute Capability
GeForce GT 420M	                2.1
```

---

### Post by Yellow Pasque on 2020-03-25
> **u666sa said:**
> Because CUDA 9.1 is not supported by GeForce 420M.

True, but CUDA 8.0.x is supported: [https://developer.nvidia.com/cuda-80-ga2-download-archive](https://developer.nvidia.com/cuda-80-ga2-download-archive)
I just did a trial run on my KDE Neon install (which is using Ubuntu 18.04.x as a base) and was able to get the samples running. I don't think the kernel version is too important if you don't try to install the driver from the CUDA .run file, which you SHOULD NOT do. Stick with the driver in the Ubuntu repo.

The install is a bit of a pain though. You have to install gcc/g++ 5.x before installation: 
```
sudo apt-get install gcc-5 g++-5 libmodule-install-perl
```
I also ran into this issue: [https://forums.developer.nvidia.com/t/cant-locate-installutils-pm-in-inc/46952](https://forums.developer.nvidia.com/t/cant-locate-installutils-pm-in-inc/46952)
After install, don't forget to make symlinks for gcc-5 and g++-5 in /usr/local/cuda-8.0/bin because nvcc will not work without them.
```
cd /usr/local/cuda-8.0/bin
ln -s /usr/bin/gcc-5 gcc
ln -s /usr/bin/g++-5 g++
```

> You boys need a highly visible guide on selecting proper cuda version and installing it. 

That info isn't Ubuntu-specific: [https://en.wikipedia.org/wiki/CUDA#GPUs_supported](https://en.wikipedia.org/wiki/CUDA#GPUs_supported)
Also, from Ubuntu's POV, users should use the CUDA version found in their repo. Hacking around the limits of your GPU by installing older versions of CUDA from a .run file isn't something Ubuntu (or Nvidia) is going to encourage or officially support.

---

