---
title: "OpenGL on NVidia card"
date: 2014-02-06
forum: Hardware
---

### Post by zozio32 on 2014-02-06
Hi,

I can't get Darktable to run with OpenGL on my computer.
I am running 13.04, and my GPU is a NVidia GeForce GT 630 OEM.

I went on the darktable page, and they say to look into etc/OpenGL/   I indeed found a subfolder, vendors, and in it a file "nvidia.icd"
There is only one line into this file: libnvidia-opencl.so.1

any idea what I should do?

btw, that's what I am getting when trying to run darktable from the command line with opencl related info:

```

zozio@ZozioJogafePC:~$ darktable -d opencl
[opencl_init] opencl related configuration options:
[opencl_init] 
[opencl_init] opencl: 1
[opencl_init] opencl_library: ''
[opencl_init] opencl_memory_requirement: 768
[opencl_init] opencl_memory_headroom: 300
[opencl_init] opencl_device_priority: '*/!0,*/*/*'
[opencl_init] opencl_size_roundup: 16
[opencl_init] opencl_async_pixelpipe: 0
[opencl_init] opencl_synch_cache: 0
[opencl_init] opencl_number_event_handles: 25
[opencl_init] opencl_micro_nap: 1000
[opencl_init] opencl_use_pinned_memory: 0
[opencl_init] opencl_use_cpu_devices: 0
[opencl_init] opencl_avoid_atomics: 0
[opencl_init] opencl_omit_whitebalance: 0
[opencl_init] 
[opencl_init] trying to load opencl library: '<system default>'
[opencl_init] opencl library 'libOpenCL' found on your system and loaded
[opencl_init] could not get platforms: -1001
[opencl_init] FINALLY: opencl is NOT AVAILABLE on this system.
[opencl_init] initial status of opencl enabled flag is OFF.

```

---

### Post by zozio32 on 2014-02-07
any idea what to do?

---

