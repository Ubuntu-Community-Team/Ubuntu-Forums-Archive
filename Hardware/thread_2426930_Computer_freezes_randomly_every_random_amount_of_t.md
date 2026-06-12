---
title: "Computer freezes randomly every random amount of time, nvidia GPU? ubuntu 18.04"
date: 2019-09-15
forum: Hardware
---

### Post by jafshredder on 2019-09-15
I have a gtx 1060 and I've been experiencing total freezes every X amount of hours at the time that makes me reboot all the time. 

**dkms status**

```
nvidia, 435.21, 4.15.0-60-generic, x86_64: installed
nvidia, 435.21, 5.0.0-23-generic, x86_64: installed
rtl8812au, 4.3.8.12175.20140902+dfsg, 4.15.0-60-generic, x86_64: installed
rtl8812au, 4.3.8.12175.20140902+dfsg, 5.0.0-23-generic, x86_64: installed
rtl8812au, 5.3.4, 4.15.0-60-generic, x86_64: built
rtl8812au, 5.3.4, 5.0.0-23-generic, x86_64: built
system76, 1.0.6~1565098100~18.04~f887e02, 4.15.0-58-generic, x86_64: installed
system76, 1.0.6~1565098100~18.04~f887e02, 4.15.0-60-generic, x86_64: installed
system76, 1.0.6~1565098100~18.04~f887e02, 5.0.0-21-generic, x86_64: installed
system76, 1.0.6~1565098100~18.04~f887e02, 5.0.0-23-generic, x86_64: installed
system76-io, 1.0.1~1559663713~18.04~ea5f61a, 4.15.0-58-generic, x86_64: installed
system76-io, 1.0.1~1559663713~18.04~ea5f61a, 4.15.0-60-generic, x86_64: installed
system76-io, 1.0.1~1559663713~18.04~ea5f61a, 5.0.0-21-generic, x86_64: installed
system76-io, 1.0.1~1559663713~18.04~ea5f61a, 5.0.0-23-generic, x86_64: installed
virtualbox, 5.2.32, 4.15.0-60-generic, x86_64: installed
virtualbox, 5.2.32, 5.0.0-23-generic, x86_64: installed

```

**dpkg -l nvidia***

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  nvidia-304     <none>       <none>       (no description available)
un  nvidia-340     <none>       <none>       (no description available)
un  nvidia-384     <none>       <none>       (no description available)
un  nvidia-390     <none>       <none>       (no description available)
un  nvidia-common  <none>       <none>       (no description available)
ii  nvidia-compute 435.21-1pop1 amd64        Transitional package for nvidia-c
ii  nvidia-compute 435.21-1pop1 amd64        NVIDIA compute utilities
ii  nvidia-dkms-43 435.21-1pop1 amd64        Transitional package for nvidia-d
ii  nvidia-dkms-43 435.21-1pop1 amd64        NVIDIA DKMS package
un  nvidia-dkms-ke <none>       <none>       (no description available)
ii  nvidia-driver- 435.21-1pop1 amd64        Transitional package for nvidia-d
ii  nvidia-driver- 435.21-1pop1 amd64        Transitional package for nvidia-d
ii  nvidia-driver- 435.21-1pop1 amd64        NVIDIA driver metapackage
un  nvidia-driver- <none>       <none>       (no description available)
un  nvidia-kernel- <none>       <none>       (no description available)
ii  nvidia-kernel- 435.21-1pop1 amd64        Transitional package for nvidia-k
ii  nvidia-kernel- 435.21-1pop1 amd64        Shared files used with the kernel
un  nvidia-kernel- <none>       <none>       (no description available)
ii  nvidia-kernel- 435.21-1pop1 amd64        Transitional package for nvidia-k
ii  nvidia-kernel- 435.21-1pop1 amd64        NVIDIA kernel source package
un  nvidia-legacy- <none>       <none>       (no description available)
un  nvidia-opencl- <none>       <none>       (no description available)
un  nvidia-persist <none>       <none>       (no description available)
un  nvidia-prime   <none>       <none>       (no description available)
ii  nvidia-setting 390.77-0ubun amd64        Tool for configuring the NVIDIA g
un  nvidia-setting <none>       <none>       (no description available)
un  nvidia-smi     <none>       <none>       (no description available)
un  nvidia-utils   <none>       <none>       (no description available)
ii  nvidia-utils-4 435.21-1pop1 amd64        Transitional package for nvidia-u
ii  nvidia-utils-4 435.21-1pop1 amd64        NVIDIA driver support binaries
un  nvidia-vdpau-d <none>       <none>       (no description available)

```

any idea what could be wrong with my system? I run a health check on my 240gb kingston ssd and it says 96%

Any wrong about my nvidia configuration?

---

### Post by Autodave on 2019-09-15
I seriously doubt that the problem is the GPU.  It sounds to me more like a heat problem, a RAM issue, or a power supply issue.

Check fans for proper operation and dirt build-up.  Check CPU cooler for being clogged with dust / dirt.  Leave side panel off and see if that helps.  You could also blow some fresh air in with a fan.

Run memtest and do a full test (which will take awhile).

For the power supply, disaconnect all devices except your keyboard and mouse and see if that helps.

---

