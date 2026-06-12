---
title: "linux-image-generic hosed system"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2009-03-27
I have been upgraded my 8.10 install. Everything seemed to be working well. I had nvidia drivers 177 working.

After upgrading linux-image-generic (best of my knowledge), I now receive the following error:
Failed to load moduel type1
NVIDIA (0) FAILED TO LOAD NVIDIA KERNAL

Also, I have two entries in my grub.
One for -2.6.27-11
and one for -2.6.27-7

I attempted the following:
sudo nvidia-xconfig

gksu nvidia-settings
Did not help. So I am running now in low-res.

I plan on re-installing 8.10 ... BUT... what should or should I not do? Why do I have two kernels?

---

### Post by upchucky on 2009-03-27
8.10 is not a long term release, it has issues with 3d, and specific issues with nvidia, there are workarounds, but you are better to use 8.04


when up and running check which kernal is running and delete the other from grub

---

### Post by snova on 2009-03-27
> **pjmlmas said:**
> I have been upgraded my 8.10 install. Everything seemed to be working well. I had nvidia drivers 177 working.

After upgrading linux-image-generic (best of my knowledge), I now receive the following error:
Failed to load moduel type1
NVIDIA (0) FAILED TO LOAD NVIDIA KERNAL

Also, I have two entries in my grub.
One for -2.6.27-11
and one for -2.6.27-7

Try booting the older one.

> I plan on re-installing 8.10 ... BUT... what should or should I not do? Why do I have two kernels?

Because apt does not remove old kernels; they must be removed manually.

---

### Post by norwoods on 2009-03-27
when you updated your system it added a newer kernel.  the driver interface to the kernel was compiled for the older kernel and did not work with the newer kernel.  this is the problem with installing things by a method other than through apt or synaptic.

i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

---

### Post by pjmlmas on 2009-03-28
Synaptic was utilized. I was updating section by section using Synaptic just for such issues...dependents are pulled in AND I can trace which updates causes an issue. I will attempt to install the driver package listed, as well as try to boot old kernel. The older kernel will still "have" the updates I have been installing?

---

