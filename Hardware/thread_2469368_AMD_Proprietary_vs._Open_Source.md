---
title: "AMD Proprietary vs. Open Source"
date: 2021-11-26
forum: Hardware
---

### Post by Shibblet on 2021-11-26
Just got a new computer, and it has an AMD Vega 8 iGPU.

I am only previously acquainted with Nvidia's Drivers, and the whole cluster-fart that is Nouveau...

I have read that the Open Source AMD Video Drivers are "baked into" the Kernel from this thread:  [https://ubuntuforums.org/newreply.php?do=newreply&p=14054442]("https://ubuntuforums.org/newreply.php?do=newreply&p=14054442")

> **QIII said:**
> With AMD graphics, there are only two driver modules:  the open-source radeon and open-source amdgpu (onto which the proprietary AMDGPU_PRO may be added.)  Both drivers are modules already baked into the Linux kernel.  At install time, Ubuntu's installer determines which module supports your GPU (in this case the radeon module) and activates it.  There is no need for you to do anything further.

Apologies for picking on you here QIII.  ;-)

However, my question is, what are the main differences for AMD CPU and GPU Proprietary Drivers, as compared to the Open Source ones that are "baked into" the Kernel.  Will there be performance increases by using the Proprietary Drivers over the Open Source ones?  Glitches, issues, problems, etc... 

I know with Nvidia, the differences between the Nouveau and Proprietary Driver Performance is almost night and day.

---

### Post by QIII on 2021-11-26
The *open source* amdgpu is written by AMD.  Aside from that, there is the community developed radeon driver, a module that is also already baked into the kernel.  AMD and Canonical have had a long term love affair, which led to AMD doing all their Linux testing on Ubuntu and their releases first being available on Ubuntu.  Eventually that led to amdgpu being included in the common Linux kernel when Catalyst development and support were dropped.

However, AMD does offer the proprietary AMDGPU-PRO overlay to amdgpu.  That provides some more powerful goodies.

For most people, the standard amdgpu driver module will be sufficient.

That all said:  As with anything brand new, it may take a while for new hardware to be supported in Linux.

---

### Post by Shibblet on 2021-11-26
> **QIII said:**
> The *open source* amdgpu is written by AMD.  Aside from that, there is the community developed radeon driver, a module that is also already baked into the kernel.  AMD and Canonical have had a long term love affair, which led to AMD doing all their Linux testing on Ubuntu and their releases first being available on Ubuntu.  Eventually that led to amdgpu being included in the common Linux kernel when Catalyst development and support were dropped.

However, AMD does offer the proprietary AMDGPU-PRO overlay to amdgpu.  That provides some more powerful goodies.
Excellent.  Thank you for the information.

> **QIII said:**
> For most people, the standard amdgpu driver module will be sufficient.
What kind of people would need the AMDGPU-PRO drivers?

> **QIII said:**
> That all said:  As with anything brand new, it may take a while for new hardware to be supported in Linux.
Yes... yes it does.

---

### Post by mastablasta on 2021-11-29
my kid has AMD vega 8. all linux native and windows games (via proton) so far work without issues.

as i understand the pro is needed for some specialised use (like industrial design etc.) however for gaming and such the opensource provides good performance. you need 5.4 or higher kernel for vega 8.

---

### Post by Yellow Pasque on 2021-11-30
> **Shibblet said:**
> What kind of people would need the AMDGPU-PRO drivers?

Mostly people who are interested in GPGPU (i.e. OpenCL).

---

