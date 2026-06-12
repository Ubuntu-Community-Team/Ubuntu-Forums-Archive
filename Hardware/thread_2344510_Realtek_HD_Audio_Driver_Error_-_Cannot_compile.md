---
title: "Realtek HD Audio Driver Error - Cannot compile"
date: 2016-11-26
forum: Hardware
---

### Post by Noah_Overcash on 2016-11-26
Hi,
I am attempting to install the Realtek HD audio drivers onto my ubuntu install, however it returns compile errors.
I have a HP 17-g121wm, and cannot make either the internal B&O Play speakers or headphone jack work.

I downloaded the drivers from Realtek's (antique) site, and attempted to install.
I extracted the file, and per the instructions ran ./configure.  That worked fine, but I was unable to run `make`.
It was saying that warnings were logged as errors, causing failure.  I modified the makefile to add the -w flag to gcc in order to suppress these.
However, further into compiling, I run into errors:
```

make[2]: Leaving directory '/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/firewire'
make[1]: Leaving directory '/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa'
make -C /lib/modules/4.8.0-27-generic/build SUBDIRS=/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-27-generic'
  CC [M]  /home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.o
/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c: In function ‘snd_pcm_aio_read’:
/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c:2997:33: error: dereferencing pointer to incomplete type ‘const struct iovec’
  if (!frame_aligned(runtime, iov->iov_len))
                                 ^~
/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c:3004:3: error: invalid use of undefined type ‘struct iovec’
   bufs[i] = iov[i].iov_base;
   ^~~~
/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c: In function ‘snd_pcm_aio_write’:
/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c:3047:3: error: invalid use of undefined type ‘struct iovec’
   bufs[i] = iov[i].iov_base;
   ^~~~
/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c: At top level:
/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c:3751:3: error: unknown field ‘aio_write’ specified in initializer
   .aio_write =  snd_pcm_aio_write,
   ^
/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c:3775:3: error: unknown field ‘aio_read’ specified in initializer
   .aio_read =  snd_pcm_aio_read,
   ^
scripts/Makefile.build:289: recipe for target '/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.o' failed
make[3]: *** [/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.o] Error 1
scripts/Makefile.build:440: recipe for target '/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore' failed
make[2]: *** [/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore] Error 2
Makefile:1489: recipe for target '_module_/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa' failed
make[1]: *** [_module_/home/caroline/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-27-generic'
Makefile:170: recipe for target 'compile' failed
make: *** [compile] Error 2


```

What can I do to resolve this?

---

### Post by Yellow Pasque on 2016-11-26
Forget about Realtek's Linux audio drivers. You're wasting your time with them. They're too old to build with modern kernels and they're not going to solve your issue anyway.

Start here by giving more information: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Noah_Overcash on 2016-11-28
Here ya go:
[http://www.alsa-project.org/db/?f=03226b903c14b41ce153fa1792ee7ae0f3cd39ff](http://www.alsa-project.org/db/?f=03226b903c14b41ce153fa1792ee7ae0f3cd39ff)

---

### Post by Yellow Pasque on 2016-11-29
```
Driver version:     
Library version:    1.1.2
Utilities version:  1.1.2
```

You're missing the kernel sound module (probably as a result of something you did to try to fix your issue). Try reinstalling kernel image and loading sound module manually:
```
sudo update-pciids
sudo apt-get install --reinstall linux-image-`uname -r`
sudo modprobe -v snd-hda-intel
pulseaudio -k&
```

Does the modprobe command return any output?

---

