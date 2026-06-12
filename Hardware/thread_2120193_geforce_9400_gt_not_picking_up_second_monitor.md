---
title: "geforce 9400 gt not picking up second monitor"
date: 2013-02-25
forum: Hardware
---

### Post by takuie on 2013-02-25
Greetings All! 

I have been beating my head against the wall and cannot get my second monitor to detect in ubuntu 12.04  I have scoured the forums, tried many things but cannot seem to get it to pick up.  Got close a couple of times...

Right now, I am back to running just the generic out of the box ubuntu video driver.  I've tried the nvidia x server, but get this message when i try it...

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."  (which i did run it as root, but still got same message after restarting box and trying again).

I was getting this message even when I was using one of the drivers from the additional drivers gui

Anyways, I have an nvidia geforce 9400 gt.  here is my paste from sudo lshw -C video.  Any help would be greatly appreciated!

takuie@takuie-PC:~$ sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:fc000000-fcffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:dc80(size=128) memory:fde00000-fde7ffff

---

### Post by takuie on 2013-02-25
Nevermind, I got it.  I went back to the "beginning" and started activating the drivers 1 at a time till i finally got it to work.  still having issues with nvidia x server, but thats another ball of wax.

---

