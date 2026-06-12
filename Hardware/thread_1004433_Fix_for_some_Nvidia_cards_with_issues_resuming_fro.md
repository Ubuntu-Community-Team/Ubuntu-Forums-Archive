---
title: "Fix for some Nvidia cards with issues resuming from hibernate"
date: 2008-12-07
forum: Hardware
---

### Post by mickbuntu on 2008-12-07
Hello all,

So I was having problem with hibernate on my machine. I ended up fixing it. Using google and Ubuntu's properties list of sites. You may find this information useful for the same issue. It may work in some of your cases but no guarantee. I thought to share it in case it helps anyone else.-- Enjoy!

My bug report [https://bugs.launchpad.net/ubuntu/+bug/255601](https://bugs.launchpad.net/ubuntu/+bug/255601) and repost of it below:

> 


I fixed the problem, however the credits are not due to me. Although my pc is not a laptop the problem is the same. It is as a result of corruption see: [[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-q.htm]l](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-q.htm]l)

 Instructions From: [[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend) ]

This must be added in xorg.conf:

[B]Section "Device"
        ...
        Option "NvAGP" "1"
EndSection[/B]

References:

1. [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/92835](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/92835)
2. [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/34043](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/34043)
3. [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)
4. [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-q.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-q.html)

**_Details on the problem from Nvidia:_**
"sometimes chipsets lose their AGP configuration during suspend, and may cause corruption on the bus upon resume. The AGP driver is required to save and restore relevant register state on such systems; NVIDIA's NvAGP is notified of power management events and ensures its configuration is kept intact across suspend/resume cycles."




---

