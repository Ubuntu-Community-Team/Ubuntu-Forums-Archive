---
title: "List of all restricted binary drivers/modules"
date: 2009-11-17
forum: Hardware
---

### Post by komputes on 2009-11-17
Hi Guys,

I am creating a bootable installation of ubuntu karmic on a USB key with ubuntu that I will plug into any computer. I would like to load this key with all the available restricted modules so that they don't have to be downloaded/installed on the computer itself as they will not have a net connection.

Is there a list of all the restricted drivers, or possibly all the driver packages proposed by jockey (Hardware Drivers). I'm looking for binary driver packages for all video, network, sound, disk controllers, integrated devices.

Some of these would be:
b43-fwcutter
nvidia-glx-185
nvidia-glx-180
nvidia-glx-173
nvidia-glx-96

If you know any other binary drivers in karmic please share its package name in this thread.

Edit:

I looked up the package list for the restricted: [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz) and this is what I found:

bcmwl-kernel-source
fglrx-amdcccle
fglrx-kernel-source
nvidia-173-kernel-source
nvidia-180-kernel-source
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-185-kernel-source
nvidia-185-libvdpau
nvidia-185-libvdpau-dev
nvidia-96-kernel-source
nvidia-glx-173
nvidia-glx-173-dev
nvidia-glx-180
nvidia-glx-180-dev
nvidia-glx-185
nvidia-glx-185-dev
nvidia-glx-96
nvidia-glx-96-dev
nvidia-kernel-common
sl-modem-daemon
xorg-driver-fglrx
xorg-driver-fglrx-dev

---

### Post by Martje_001 on 2009-12-31
You can't install both fglrx and nvidia on one system. They conflict.

Search for 'fgrlx' in Synaptic and look up it's properties (dependencies).

---

