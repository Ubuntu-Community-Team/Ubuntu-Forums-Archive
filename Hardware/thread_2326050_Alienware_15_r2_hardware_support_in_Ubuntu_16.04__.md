---
title: "Alienware 15 r2 hardware support in Ubuntu 16.04 / Modern distros?"
date: 2016-05-27
forum: Hardware
---

### Post by wayne17 on 2016-05-27
We're looking at buying an Alienware 15 r2 laptop for my sister. I have been unable to find a clear answer: How well does it work in Ubuntu 16.04? or is there a better distro for this laptop? (Preferably Debian based.)  

 Please list all cons and caveats to getting Linux running on it.   

 The hardware configuration we're looking at buying is as follows:  

 CPU: i7-6700HQ 
GPU: NVIDIA® GeForce® GTX 970M with 3GB GDDR5 
Default OS: Windows 10 Home 64bit 
HHD: 1TB 7200RPM SATA (We're thinking about adding the 128GB M.2 SATA SSD to the configuration as well.)
Wifi + Bluetooth: 1535 802.11ac 2x2 WiFi and Bluetooth 4.1 
RAM: 16GB Dual Channel DDR4 at 2133MHz  

  Thanks!

---

### Post by C0derBear on 2016-06-08
My wife has a 15r2 machine and overall things work well with Ubuntu 16.04 64-bit Desktop edition, but there are caveats, at least one significant/unresolved for us

- we had no use for dual-boot Windows+Ubuntu so didn't keep Windows, no problems install/booting Ubuntu off the NVMe SSD though
- we have a problem where the device can go into sleep/hibernate, and initially comes out, but then freezes shortly after resume (filesystem goes R/O or inaccessible - very hard to diagnose), *unresolved*
- the Killer-N WiFi was never made happy when we initially put on 15.10, so I replaced with it with an Intel 7260 card which works OOTB in all cases
- my wife has not yet significantly tested using the DP output to a monitor, but that's coming, so YMMV

The resume may be a configuration issue, maybe not, we don't know yet.

---

### Post by rurounisxw on 2016-10-26
Hi, I have the same issue of sleep and crash on an nvme ssd and wonder if you have any solution yet. Ubuntu 16.04 works fine on my other sata ssd though.

---

### Post by C0derBear on 2016-10-27
I have tried a number of kernels from mainline / upstream, and a number of boot parameter tweaks, to no avail.

I just can't get my wife's computer to STOP taking the nvme offline after resume. *angry*

I may be buying her a SATA SSD just for the purposes of migrating her OS boot to that and using the nvme for secondary storage.

Not optimal, but probably will work better.

---

