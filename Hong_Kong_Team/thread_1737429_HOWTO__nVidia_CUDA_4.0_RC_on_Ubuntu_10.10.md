---
title: "HOWTO : nVidia CUDA 4.0 RC on Ubuntu 10.10"
date: 2011-04-23
forum: Hong Kong Team
---

### Post by samiux on 2011-04-23
If you have nVidia card that have several CUDAs on the card, you will interested in this tutorial.  This time, I would like to show you how to install CUDA 4.0 RC on Ubuntu 10.10 Desktop.  

You will experience faster desktop after the installation of CUDA 4.0.  Meanwhile, if you installed SMPlayer, you can playback 1080p videos with the help of vdpau.

[Here we go ....]("http://samiux.blogspot.com/2011/04/howto-nvidia-cuda-40-rc-on-ubuntu-1010.html")

Samiux

---

### Post by samiux on 2011-04-24
**HOWTO : nVidia CUDA 4.0 RC on Ubuntu Server 10.10**

If you have nVidia display card that have several CUDAs on it, you will interested in this tutorial. This time, I would like to show you how to install CUDA 4.0 RC on Ubuntu 10.10 Server.

You will experience a faster server after the installation of CUDA 4.0.

This HOWTO does not require to install X.

[Here you are ...]("http://samiux.blogspot.com/2011/04/howto-nvidia-cuda-40-rc-on-ubuntu.html")

Samiux

---

### Post by samiux on 2011-07-12
Please be informed that the tutorials are updated as the following :

CUDA Toolkit 4.0 for Desktop is [here]("http://samiux.blogspot.com/2011/05/howto-nvidia-cuda-toolkit-40-on-ubuntu.html").

CUDA Toolkit 4.0 for Server is [here]("http://samiux.blogspot.com/2011/05/howto-nvidia-cuda-toolkit-40-on-ubuntu_29.html").

Enjoy!

Samiux

---

### Post by indianabones on 2011-07-28
Superb step by step tutorial Samiux. Although I had some minor glitches, they were because of my stupidity, I re-installed Ubuntu, since I only use it for CUDA and I tried again and it works.

So THANK YOU very much for providing a very easy to follow tutorial.

---

### Post by samiux on 2011-07-29
@indianabones,

You're welcome!

Samiux

---

### Post by skidzo on 2012-01-06
Hi I tried installing on Kubuntu 11.10 but when making the SDK I get:

make[1]: *** [../../bin/linux/release/threadFenceReduction] Fehler 1
make[1]: Verlasse Verzeichnis '/home/jeckstein/NVIDIA_GPU_Computing_SDK/C/src/threadFenceReduction'
make: *** [src/threadFenceReduction/Makefile.ph_build] Fehler 2
jeckstein@seriphos:~/NVIDIA_GPU_Computing_SDK/C$ cd NVIDIA_GPU_computing_SDK/C/bin/linux/release

and before there are erros from getNumBlocksAndThreads() and that's why I think something is missing in the driver installation, most probably the driver is not active yet...

what can I do?

---

### Post by samiux on 2012-01-15
> **skidzo said:**
> Hi I tried installing on Kubuntu 11.10 but when making the SDK I get:

make[1]: *** [../../bin/linux/release/threadFenceReduction] Fehler 1
make[1]: Verlasse Verzeichnis '/home/jeckstein/NVIDIA_GPU_Computing_SDK/C/src/threadFenceReduction'
make: *** [src/threadFenceReduction/Makefile.ph_build] Fehler 2
jeckstein@seriphos:~/NVIDIA_GPU_Computing_SDK/C$ cd NVIDIA_GPU_computing_SDK/C/bin/linux/release

and before there are erros from getNumBlocksAndThreads() and that's why I think something is missing in the driver installation, most probably the driver is not active yet...

what can I do?

Hi,

The caption mentioned PPA is for 11.04 only.  If you want to install CUDA SDK on 11.10, you may consider to install the nVidia Official driver from her official website.  Maybe you can refer the following link for hints :

[http://samiux.blogspot.com/2011/12/howto-backtrack-5-r1-on-intel-x79.html]("http://samiux.blogspot.com/2011/12/howto-backtrack-5-r1-on-intel-x79.html")

Samiux

---

