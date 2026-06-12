---
title: "No nvidia-352-uvm package in Ubuntu 14.04 or 15.10"
date: 2015-11-24
forum: Hardware
---

### Post by ragtag on 2015-11-24
There is no nvidia-352-uvm package in Ubuntu 14.04 LTS, while there is one for older versions of the driver. Does this mean the NVIDIA Universal Memory features have been packaged in the nvidia-352 or libcuda1-352, or is it just missing?

I want to get working CUDA support, preferably without resorting to manual install or alternate PPAs. The 352.63 driver that is in the official repos is [Nvidia's latest Long Lived Branch]("http://www.nvidia.com/object/unix.html") version....which seems like a good choice when you don't want to be on the very bleeding edge.

---

### Post by ragtag on 2015-11-24
I'm just going to reply to my own post here. ):P

It seems the uvm package is included in one of the other packages. So with nvidia-modprobe installed, CUDA works as it should, and the /dev/nvidia-uvm device shows up when needed.

As a side note, if you're looking to use CUDA in Blender under Ubuntu 14.04, you need to get Blender from blender.org. It seems the version in Ubuntu's repository is not compiled with CUDA support.

---

