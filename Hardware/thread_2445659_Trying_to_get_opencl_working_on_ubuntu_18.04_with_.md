---
title: "Trying to get opencl working on ubuntu 18.04 with AMD R9 280X"
date: 2020-06-17
forum: Hardware
---

### Post by herbally on 2020-06-17
Attempting to get opencl working with ubuntu 18.04 with AMD  R9 280X.  Tried rocm only to discover that apparently my processor isn't supported so I've moved on to the amdgpu-pro driver in hopes of getting opencl going with it.  Unfortunately, I keep getting errors about unmet dependencies, and while I know a little about linux, I don't know enough to resolve these issues. Hoping for some guidance from the experts. Thanks in advance.

```
brett@brett-MS-7576:~/Desktop/amdgpu-pro-19.10-785425-ubuntu-18.04$ sudo ./amdgpu-pro-install -y -opencl=legacy
deb [ trusted=yes ] file:/var/opt/amdgpu-pro-local/ ./
Get:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Ign:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg            
Ign:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg       
Hit:4 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Hit:6 http://repo.radeon.com/rocm/apt/debian xenial InRelease                  
Get:7 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [969 kB]
Get:10 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages [486 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [694 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [295 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1,081 kB]
Get:14 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [748 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [1,018 kB]
Get:16 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [46.0 kB]
Get:17 http://security.ubuntu.com/ubuntu bionic-security/universe i386 Packages [624 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [279 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [213 kB]
Get:20 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [673 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:22 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,972 B]
Get:23 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [49.2 kB]
Get:24 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Fetched 7,439 kB in 7s (1,002 kB/s)                                            
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
amdgpu-pro-pin is already the newest version (19.10-785425).
Selected version '19.10-785425' (localhost [all]) for 'amdgpu-pro-pin'
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 amdgpu-hwe : Depends: amdgpu-dkms (= 19.10-785425) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

---

### Post by Yellow Pasque on 2020-06-18
Your GPU is not supported by Pro driver: [https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20)

---

### Post by herbally on 2020-06-18
> **Yellow Pasque said:**
> Your GPU is not supported by Pro driver: [https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20)

Thanks for your response. While I realize that the 280X isn't listed explicitly as supported, very similar cards are which suggests that, perhaps, it will work with the 280X.  It is, in fact, using the open source amdgpu driver.

Nevertheless, my question is related to the unmet dependencies issue encountered when I attempt to install the driver rather than the functionality of the driver after install. Is it your opinion that the lack of explicit support is causing the unmet dependencies issue or is that a separate problem someone could help me tackle?  Thanks again.

---

### Post by Yellow Pasque on 2020-06-18
> **herbally said:**
> While I realize that the 280X isn't listed explicitly as supported, very similar cards are which suggests that, perhaps, it will work with the 280X.

I wouldn't get my hopes up. The supported RX 200 cards in the list are based on newer GCN generations than the 280X. The 280X is basically a rebadged RadeonHD 7970 (GCN 1.0). Isn't marketing great?
[https://en.wikipedia.org/wiki/List_of_AMD_graphics_processing_units#Radeon_R5/R7/R9_200_series](https://en.wikipedia.org/wiki/List_of_AMD_graphics_processing_units#Radeon_R5/R7/R9_200_series)

> It is, in fact, using the open source amdgpu driver.
Are you sure about that? The last time I checked, GCN 1.0/1.1 cards defaulted to the older radeon kernel module, though one could force amdgpu kernel module using kernel boot options. Maybe check this to find out:
```
lspci -k
```

> Nevertheless, my question is related to the unmet dependencies issue encountered when I attempt to install the driver rather than the functionality of the driver after install. Is it your opinion that the lack of explicit support is causing the unmet dependencies issue or is that a separate problem someone could help me tackle?

I don't have enough personal experience with amdgpu-pro to answer that. However, I think you are asking the wrong question. You should be following the removal procedure: [https://amdgpu-install.readthedocs.io/en/latest/install-installing.html#uninstalling-the-amdgpu-graphics-stack](https://amdgpu-install.readthedocs.io/en/latest/install-installing.html#uninstalling-the-amdgpu-graphics-stack) and getting rid of any "amdgpu-pro" packages if any are left behind.
For OpenCL, probably the best you can hope to do on this card is the mesa/libclc implementation:
```
sudo apt-get install mesa-opencl-icd
```
It only supports OpenCL 1.1 though, so if you are trying to do something that requires OpenCL >= 1.2, you may be out of luck.

---

### Post by herbally on 2020-06-18
Well hell...I was hoping for better news my friend.  For what its worth, "lspci -v" produces the following.

```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X] (prog-if 00 [VGA controller])
    Subsystem: XFX Pine Group Inc. Tahiti XTL [Radeon R9 280X]
    Flags: bus master, fast devsel, latency 0, IRQ 30, NUMA node 0
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe9c0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at c000 [size=256]
    Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: amdgpu
    Kernel modules: radeon, amdgpu
```

So you think I'm SOL, huh? :cry:

---

### Post by Yellow Pasque on 2020-06-18
> Kernel driver in use: amdgpu
Interesting. I could have sworn amdgpu was still "experimental" for GCN 1.0 cards. Did you manually force it to load with boot parameters, or was it loaded automatically?
At any rate, just having amdgpu is not enough for OpenCL.

> So you think I'm SOL, huh?

In terms of using anything other than the mesa OpenCL 1.1 or CPU/software-based OpenCL, yes.

For why no ROCM, see notes on GCN 1.0/Tahiti:
[https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/open-source-amd-linux/867677-setting-up-the-radeon-open-compute-platform-on-linux?p=867815#post867815](https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/open-source-amd-linux/867677-setting-up-the-radeon-open-compute-platform-on-linux?p=867815#post867815)

---

