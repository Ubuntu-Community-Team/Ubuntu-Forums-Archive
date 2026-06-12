---
title: "Installing xfce in ARM chroot fails on a few packages"
date: 2014-02-10
forum: Hardware
---

### Post by zacthespack2 on 2014-02-10
When I try to install xfce within my ARM chroot, I end up with:

```
Err http://ports.ubuntu.com/ saucy/main libfuse2 armhf 2.9.2-4ubuntu2  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libsystemd-daemon0 armhf 204-0ubuntu15
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libapparmor1 armhf 2.8.0-0ubuntu30
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libsystemd-login0 armhf 204-0ubuntu15
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main dbus armhf 1.6.12-0ubuntu8
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main systemd-services armhf 204-0ubuntu15
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libpam-systemd armhf 204-0ubuntu15
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main fuse armhf 2.9.2-4ubuntu2
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libwayland-client0 armhf 1.1.0-2ubuntu2
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libwayland-cursor0 armhf 1.1.0-2ubuntu2
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libgl1-mesa-dri armhf 9.2.1-1ubuntu1
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libwayland-server0 armhf 1.1.0-2ubuntu2
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libgbm1 armhf 9.2.1-1ubuntu1
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libegl1-mesa armhf 9.2.1-1ubuntu1
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libopenvg1-mesa armhf 9.2.1-1ubuntu1
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libegl1-mesa-drivers armhf 9.2.1-1ubuntu1
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main dbus-x11 armhf 1.6.12-0ubuntu8
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libgomp1 armhf 4.8.1-10ubuntu7
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libgstreamer-plugins-base1.0-0 armhf 1.2.0-1
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libgudev-1.0-0 armhf 1:204-0ubuntu15
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libupower-glib1 armhf 0.9.22-1
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main cpp-4.8 armhf 4.8.1-10ubuntu7
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main cpp armhf 4:4.8.1-2ubuntu2
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main desktop-file-utils armhf 0.21-1ubuntu1
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libandroid-properties1 armhf 0.1.0+git20130606+c5d897a-0ubuntu32
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libhybris-common1 armhf 0.1.0+git20130606+c5d897a-0ubuntu32
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main libhardware2 armhf 0.1.0+git20130606+c5d897a-0ubuntu32
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main upower armhf 0.9.22-1
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main x11-apps armhf 7.7+1
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main xserver-common all 2:1.14.3-3ubuntu1
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main xserver-xorg-core armhf 2:1.14.3-3ubuntu1
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main xserver-xorg-video-all armhf 1:7.7+1ubuntu5
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main xserver-xorg-input-all armhf 1:7.7+1ubuntu5
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main xserver-xorg armhf 1:7.7+1ubuntu5
  404  Not Found [IP: 91.189.88.140 80]
Err http://ports.ubuntu.com/ saucy/main xorg armhf 1:7.7+1ubuntu5
  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/f/fuse/libfuse2_2.9.2-4ubuntu2_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/s/systemd/libsystemd-daemon0_204-0ubuntu15_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/a/apparmor/libapparmor1_2.8.0-0ubuntu30_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/s/systemd/libsystemd-login0_204-0ubuntu15_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/d/dbus/dbus_1.6.12-0ubuntu8_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/s/systemd/systemd-services_204-0ubuntu15_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/s/systemd/libpam-systemd_204-0ubuntu15_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/f/fuse/fuse_2.9.2-4ubuntu2_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/w/wayland/libwayland-client0_1.1.0-2ubuntu2_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/w/wayland/libwayland-cursor0_1.1.0-2ubuntu2_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/m/mesa/libgl1-mesa-dri_9.2.1-1ubuntu1_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/w/wayland/libwayland-server0_1.1.0-2ubuntu2_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/m/mesa/libgbm1_9.2.1-1ubuntu1_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/m/mesa/libegl1-mesa_9.2.1-1ubuntu1_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/m/mesa/libopenvg1-mesa_9.2.1-1ubuntu1_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/m/mesa/libegl1-mesa-drivers_9.2.1-1ubuntu1_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/d/dbus/dbus-x11_1.6.12-0ubuntu8_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/g/gcc-4.8/libgomp1_4.8.1-10ubuntu7_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/g/gst-plugins-base1.0/libgstreamer-plugins-base1.0-0_1.2.0-1_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/s/systemd/libgudev-1.0-0_204-0ubuntu15_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/u/upower/libupower-glib1_0.9.22-1_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/g/gcc-4.8/cpp-4.8_4.8.1-10ubuntu7_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/g/gcc-defaults/cpp_4.8.1-2ubuntu2_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/d/desktop-file-utils/desktop-file-utils_0.21-1ubuntu1_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/libh/libhybris/libandroid-properties1_0.1.0+git20130606+c5d897a-0ubuntu32_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/libh/libhybris/libhybris-common1_0.1.0+git20130606+c5d897a-0ubuntu32_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/libh/libhybris/libhardware2_0.1.0+git20130606+c5d897a-0ubuntu32_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/u/upower/upower_0.9.22-1_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/x/x11-apps/x11-apps_7.7+1_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/x/xorg-server/xserver-common_1.14.3-3ubuntu1_all.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/x/xorg-server/xserver-xorg-core_1.14.3-3ubuntu1_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/x/xorg/xserver-xorg-video-all_7.7+1ubuntu5_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/x/xorg/xserver-xorg-input-all_7.7+1ubuntu5_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/x/xorg/xserver-xorg_7.7+1ubuntu5_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
Failed to fetch http://ports.ubuntu.com/pool/main/x/xorg/xorg_7.7+1ubuntu5_armhf.deb  404  Not Found [IP: 91.189.88.140 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



```

My sources.list is:

deb [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy main restricted universe
deb-src [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy main restricted universe

---

