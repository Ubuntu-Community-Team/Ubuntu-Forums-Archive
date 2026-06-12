---
title: "R9 290x ATI - installation problem for mining"
date: 2014-04-02
forum: Hardware
---

### Post by nicolasdiogo on 2014-04-02
hello,

i have tried installing the ATI R9 290x cards on a ubuntu 12.04 with minimal X installed (xdm, openbox), and it does not recognise these card.

```

lspci
...
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii XT [Radeon HD 8970]
...

```

i have downloaded the latest BETA drivers from ATI.
i tried installing by firstly creating packages for Ubuntu - precise - and then after that failure, i have also tried their own installation process.

both of these failed.

after installing the driver - whatever way.

i have the following output when testing the installation:
```

aticonfig --lsa
* 0. 02:00.0 Supported device 67B0

```

i then proceed to initialised the card with this command:
```

aticonfig --adapter=all --initial

```

at this point, i can read the xorg.conf that has the correct details for my card.

after rebooting i test the installation:
```

fglrxinfo 
display: localhost:10.0  screen: 0
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string: 1.4 (3.0 Mesa 9.2.1)

```

and i can run all the usual glxgears.

but when i try to run a mining software i find this error:
```

export DISPLAY=:0
export GPU_MAX_ALLOC_PERCENT=100
export GPU_USE_SYNC_OBJECTS=1
./sgminer -n
CL Platform 0 vendor: Advanced Micro Devices, Inc.                    
CL Platform 0 name: AMD Accelerated Parallel Processing                    
CL Platform 0 version: OpenCL 1.2 AMD-APP (1214.3)                    
Error -1: Getting Device IDs (num)                    
clDevicesNum returned error, no GPUs usable                    
0 GPU devices max detected                    
USB all: found 10 devices - listing known devices                    
No known USB devices

```


has anyone managed to have this card correctly installed on Ubuntu yet?

thanks,

---

### Post by nicolasdiogo on 2014-04-11
There are major problems that i have found when installing an ATI card.

so instead of using ATI installer, i have created DEB packages and installed those.

and it worked in the end.

is this likely to cause problems as new kernels are installed on the system?

thanks,

---

### Post by nicolasdiogo on 2014-07-13
so it required a new version of ATI to work properly

---

