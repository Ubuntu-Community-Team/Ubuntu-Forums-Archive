---
title: "trouble configuring Lenovo W520 nvidia 2000M for CUDA and OpenCL"
date: 2011-08-25
forum: Hardware
---

### Post by iapx86 on 2011-08-25
This computer is for high performance 3D physics calculations.

Following advice found elsewhere I disabled nvidia in BIOS, installed 11.04 64 bit ubuntu then rebooted, enabled nvidia, and began enjoying the system.

Then I tried installing pycuda, pygpu, pyopencl, and non-python gpu libraries of any sort with a variety of failures.

Then I attempted to use all my previous python visualizations. These all failed due to GLX not being enabled in my X.

After further research I was able to re-enable these earlier visualizations with the following commands:

sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf

Now I fear my machine probably lacks nvidia support.  I do not particularly care whether nvidia controls my screen.  I am happy to use the "Intel Integrated Graphics".  However I want to use the gpu cores on the nvidia card to perform those 3D calculations.  I also don't care if the machine heats up as it uses the gpu cores.

Question: How do I configure my machine to enable CUDA and OpenCL usage?

---

