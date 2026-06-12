---
title: "video problem"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by tesseract36 on 2007-07-25
i have 2 laptops and one has ubuntu, and i updated it to the newest distro and it was all fine and great then i tryed using desktop effects and it asked me to inststall a driver for an nvidia card for 3d graphics and acceleration. so i did and restarted my conputer and now the screen goes black right after the ubuntu loading bar finishes.

the laptop is and inspiron 18200 dell

---

### Post by pbcartwright on 2007-07-25
when you install an nvidia card you have to shut down the X-server and run sax2 to let the linux kernel know about the new video driver. Go to nvidia.com download the latest linux driver, and read the README..
It used to be you had to run sax3, now it looks like you run nvidia-xconfig:

The NVIDIA Driver includes a utility called nvidia-xconfig, which is designed to make editing the X configuration file easy. You can also edit it by hand.
Using nvidia-xconfig to configure the X server

nvidia-xconfig will find the X configuration file and modify it to use the NVIDIA X driver. In most cases, you can simply answer "Yes" when the installer asks if it should run it. If you need to reconfigure your X server later, you can run nvidia-xconfig again from a terminal. nvidia-xconfig will make a backup copy of your configuration file before modifying it.

Note that the X server must be restarted for any changes to its configuration file to take effect.

More information about nvidia-xconfig can be found in the nvidia-xconfig manual page by running.

    % man nvidia-xconfig

---

