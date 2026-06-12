---
title: "AMDGPU-PRO issues"
date: 2016-11-28
forum: Hardware
---

### Post by gtippitt on 2016-11-28
Dear QIII,

I am also having problems with my AMD RX480 graphics card.  I normally try to avoid hijacking someone's thread, but it seemed better to post in this thread rather than start another with  the same problem and subject line.  

I am running a fresh install of Ubuntu-MATE 16.04.1 and am trying to get my RX480 card working for OpenCL GPU tasks for BOINC-SETI.  I have tried this card in different machines and can't get the AMDGPU-PRO drivers to work for OpenCL GPU computing.  I have been running GPU tasks for BOINC projects with NVIDIA cards on several PC for a few years, but this is my first attempt to get it working with an AMD card.  The price per GFLOP for the RX470/80 cards were so great, I wanted to give them a try.

Your earlier post said that you have these AMD-Pro drivers working, so I wondered if there was anything required other than running the AMD install script and adding my userid to the video group as the AMD website instructs.  I using the 4.4.0-47 kernel which is up to date for 16.04.

In addition to the BOINC software not detecting the AMD GPU, the "/opt/amdgpu-pro/bin/amdgpu_test" program that is installed with the AMDGPU-PRO drivers responds with "DRM driver is not available" when I run it.    I have tried both RX470 and RX480 graphics cards with 3 different motherboards using 16.04 and 16.10 versions of plain UBUNTU and UBUNTU-MATE.  I've tried all 24 permutations 2 graphics cards, 3 motherboards, and 4 OS versions.  I get the same non-result in all cases, where the CLINFO fails to detect any GPUs.

any help? 
Thanks,
Greg

---

### Post by QIII on 2016-11-29
I have AMDGPU running right now on my 16.04 machine.  -PRO, for some reason, is not providing output to one of four monitors on that machine.  I suspect the kernel not ready for it.

On my 16.10 machine, AMDGPU-PRO is working as it should.  

I'll try to see about testing GPU-based BOINC projects this weekend.  Bear in mind that it could very well be that those who maintain software for various projects running on BOINC may not yet have accounted for the new drivers.  One thing you might try:  BOINC files belong to the user boinc, I and processes are run by that user, I believe.  The first thing I'm going to try personally if I run into problems is to add boinc to video.

The script errors being encountered sound like typographical errors not discovered prior to release.  I will also see about how this can be reported.

---

### Post by QIII on 2016-11-29
OK.  I'm on my 16.10 machine.  Here is some info:

```
dpkg -l amdgpu-pro
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  amdgpu-pro     16.30.3-3154 amd64        This package install all amdgpu-p

```

```
clinfo | grep OpenCL
  Platform Version:				 OpenCL 2.0 AMD-APP (2117.7)
    Execute OpenCL kernels:			 Yes
  Device OpenCL C version:			 OpenCL C 1.2 
  Version:					 OpenCL 1.2 AMD-APP (2117.7)
    Execute OpenCL kernels:			 Yes
  Device OpenCL C version:			 OpenCL C 1.2 
  Version:					 OpenCL 1.2 AMD-APP (2117.7)

```

This is an R9 380X -- GCN 1.2

So, yes.  AMDGPU-PRO is definitely installed and supporting OpenCL.  I'll see if I can make time to check BOINC, but it's 10:30 pm here.

Edit:  What I am seeing right now is a lot of discussion about whether AMDGPU-PRO will even work with BOINC projects yet.

Edit:  And I have Moo!Wrapper (one of the few projects I could find with ATI/AMD) recognizing the GPU in BOINC.  However, 

```
sudo cat /sys/kernel/debug/dri/64/amdgpu_pm_info
``` is showing no load on the GPU.

I don't think this indicates a lack of capability on the part of the driver or hardware, but on the need to refactor code in the BOINC projects.

Moved to a new thread as off-topic where it was.

---

### Post by gtippitt on 2016-11-29
My problem is not just with BOINC GPU jobs.  Something is very different on your machine.  The output of CLINFO is completely different.  Could you also try the "/opt/amdgpu-pro/bin/amdgpu_test"  program.
Greg

---

### Post by gtippitt on 2016-11-29
I figured out why CLINFO output was different on mine.  I was running the one installed by AMD in the /opt folder.  When I installed the one from Ubuntu repos, I get the same output as you.  In fact I get the same info when I run CLINFO on any multi-cpu AMD motherboard without any GPU.  THE AMD-APP is for multi-core CPU tasks, not AMD-GPU tasks.  I don't think your machine is working for GPU OPENCL processing either.  I'm going to search AMD's website to see if perhaps there is an SDK that may be required to get these cards working for more than simple display output.

---

### Post by QIII on 2016-11-29
There is a Vulkan SDK.

After installing the Vulkan SDK:

```
Number of platforms:				 1
  Platform Profile:				 FULL_PROFILE
  Platform Version:				 OpenCL 2.0 AMD-APP (2117.7)
  Platform Name:				 AMD Accelerated Parallel Processing
  Platform Vendor:				 Advanced Micro Devices, Inc.
  Platform Extensions:				 cl_khr_icd cl_amd_event_callback cl_amd_offline_devices 


  Platform Name:				 AMD Accelerated Parallel Processing
Number of devices:				 2
  Device Type:					 CL_DEVICE_TYPE_GPU
...

```

Now the GPU is being used for the BOINC project.

---

### Post by QIII on 2016-11-30
OK.  For 16.04 I installed kernel version 4.8 and used the script on the AMD page for installing AMDGPU-PRO.

Then, I installed the three Vulkan packages that make up the SDK from Yakkety.

This is certainly not the sort of thing I would suggest to a novice.

---

### Post by gtippitt on 2016-12-02
Definitely not for a novice!  I've been programming on UNIX based systems since 1983 on TRS-80s, running BOINC jobs on Linux for more than a decade, and getting these new AMD RX4XX cards to run OpenCL GPU tasks has eluded me for 2 months.  I'm going to give up and wait till Spring in hopes that AMD and UBUNTU will work together more easily by then.  Back to running NVIDIA cards for me, even if they cost more per GFLOP.  Well perhaps they don't cost more since I can't get the OpenCL drivers to even see the AMD GPUs. let alone to run anything.  Zero GFLOPS isn't a good deal, no matter how much cheaper AMD is that NVIDIA.

Thanks for your help QIII.  I love your donkey avatar.

---

