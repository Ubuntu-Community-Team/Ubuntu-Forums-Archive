---
title: "uestion insideX broken after update, but fixed it, extra q"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by Rackstar on 2009-08-18
Hi,

After I did the last upgrades this morning. (Kernel upgrade and Xorg upgrade I think). I needed to reboot, and then X wouldn't load.

I had installed the NVidia driver from NVidia.com (I needed the last 185 driver, because it fixes Bibble 5 issue). When installing this, it had to recompile the kernel. So I figured I needed to uninstall the driver and reinstall it. (It was still there on my desktop luckely)

And then after a reboot X came back to me. Is this normal if I install the driver from NVidia.com?

It wasn't that hard for me, but lethal for someone less experienced.

Ruben

---

### Post by tommcd on 2009-08-18
> **Rackstar said:**
> 
I had installed the NVidia driver from NVidia.com (I needed the last 185 driver, because it fixes Bibble 5 issue). When installing this, it had to recompile the kernel. So I figured I needed to uninstall the driver and reinstall it. (It was still there on my desktop luckely)

Yes it is. When you install the nvidia driver from nvidia/com, the APT package manager is unable to keep track of it because it is not a .deb package from the Ubuntu repos. So you will have to uninstall and reinstall the nvidia driver after every kernel upgrade. 
This is one of the advantages to using the nvidia driver from the nvidia repos. The driver in the repos will be reinstalled whenever there is a kernel upgrade.
If you must have the latest driver from nvidia.com, there is an Ubuntu package called **envyng** that will automatically install the nvidia driver from nvidia.com. The latest versions of envyng are said to automatically reinstall the nvidia driver with kernel upgrades. Read about it here:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Rackstar on 2009-08-18
Hi,

Thanks for the answer!

They should warn users about that on the NVidia website. A lot of new users probably go there, because they don't know about package managers yet.

---

### Post by tommcd on 2009-08-18
> **Rackstar said:**
> 
They should warn users about that on the NVidia website. A lot of new users probably go there, because they don't know about package managers yet.
They do, ...well, sort of. See part 4 of the nvidia driver README:
[http://us.download.nvidia.com/XFree86/Linux-x86/185.18.31/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.31/README/index.html)
[http://us.download.nvidia.com/XFree86/Linux-x86/185.18.31/README/chapter-04-section-03.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.31/README/chapter-04-section-03.html)
> The NVIDIA kernel module has a kernel interface layer that must be compiled specifically for each kernel.
Perhaps it could be in a more prominent place though.

---

### Post by Rackstar on 2009-08-18
Ok, I kinda missed that. 

But talking to new users about kernel interface layers... 

Thanks for pointing that out.

---

