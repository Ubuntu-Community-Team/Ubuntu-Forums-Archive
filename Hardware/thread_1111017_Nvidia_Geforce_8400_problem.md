---
title: "Nvidia Geforce 8400 problem"
date: 2009-03-30
forum: Hardware
---

### Post by blagus on 2009-03-30
Hello everyone!
I'm having a problem.
That problem probably was discussed already, but I'm too lazy to look around:lolflag:
So here's the problem.
My HDD died, with Windows where my GeForce 8400 was working perfectly.
So, without HDD, I'm running ubuntu 8.04.1 from LiveCD.
Before, when it was installed on HDD, my GeForce was detected normally in System->Administration->HW Drivers.
But now, there's nothing displayed. When I download "nvidia-glx-new" from Synaptic, it downloads OK and installs, but nothing happens when I restart X (Ctrl-Alt-Backspace). Still, nothing in "HW Drivers". Here's what I see in Terminal:
```
ubuntu@ubuntu:~$ sudo jockey-gtk
WARNING: modinfo for module nvidia_new failed: modinfo: could not open /lib/modules/2.6.24-19-generic/volatile/nvidia_new.ko: No such file or directory

WARNING: modinfo for module nvidia failed: modinfo: could not open /lib/modules/2.6.24-19-generic/volatile/nvidia.ko: No such file or directory

WARNING: modinfo for module nvidia_legacy failed: modinfo: could not open /lib/modules/2.6.24-19-generic/volatile/nvidia_legacy.ko: No such file or directory

WARNING: modinfo for module fglrx failed: modinfo: could not open /lib/modules/2.6.24-19-generic/volatile/fglrx.ko: No such file or directory

WARNING: modinfo for module nvidia_new failed: modinfo: could not open /lib/modules/2.6.24-19-generic/volatile/nvidia_new.ko: No such file or directory


```
Can you help me?
P.S. I also tried downloading from nvidia.com, but I don't know how to shut down X.

---

