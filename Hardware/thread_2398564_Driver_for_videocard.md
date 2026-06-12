---
title: "Driver for videocard"
date: 2018-08-14
forum: Hardware
---

### Post by luvuntu on 2018-08-14
Hi,

I am new to Lubuntu, ith the App ´Sysinfo¨, i was able to see that this is my video card -->> Radeon HD 6400M/7400M Series (I am not quite sure if its specific enough)

I was able to find the drivers on the following website:
[https://support.amd.com/en-us/download/linux](https://support.amd.com/en-us/download/linux)

I have a HP Pavilion G7 11060SB Laptop with 64bit alternate Lubuntu installed.
I was wondering if my Video card driver(s) was installed correctly and  if not, which driver(s) do i need and how do i install it?
As mentioned i am not sure if my video card drivers were installed correctly. How do i check if they are installed correctly?

Thanks,
LuVuntu

---

### Post by TheFu on 2018-08-14
Drivers for Linux aren't like drivers for Windows.  Unless there is a show-stopping issue, please stay with the drivers that Canonical provides.  The drivers directly from the vendors often cause terrible issues.

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) and
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
are the references.

---

### Post by luvuntu on 2018-08-14
Thanks for the advice, then i wont be installing any video card drivers.

---

### Post by TheFu on 2018-08-14
> **luvuntu said:**
> Thanks for the advice, then i wont be installing any video card drivers.

Actually, my intention was for you to click both those links and follow the advice there using your best judgement.

But if someone suggests that you visit amd.com and download files, that is poor advice.  That isn't the best method on Linux.

---

### Post by QIII on 2018-08-14
When Ubuntu is installed on a machine with an AMD GPU, the installer chooses the appropriate driver from Radeon or AMDGPU, depending on support for your GPU.

If you have a card that causes the installation of Radeon, you *typically* need do nothing more.

If the AMDGPU driver is used, you *may* get some better performance under some circumstances by installing the MESA module.  But don't do that unless it is needed.

With either of those drivers, there is really nothing more most users need to do.

The proprietary AMDGPU-PRO overlay can be installed if AMDGPU is installed, but *there really is no reason to do that* unless you have very specific needs.  Don't bother otherwise.  AMD created the AMDGPU specifically to provide an outstanding open-source driver to the Linux community.

---

### Post by Yellow Pasque on 2018-08-15
Radeon HD 6400M/7400M should work out of the box.

Check:
```
glxinfo -B
```
Make sure you don't see "llvmpipe" or "software rendering" in the output.

---

### Post by TheFu on 2018-08-15
> **Temüjin said:**
> Radeon HD 6400M/7400M should work out of the box.

Check:
```
glxinfo -B
```
Make sure you don't see "llvmpipe" or "software rendering" in the output.

glxinfo -B does show llvmpipe on my slow firefox system.  It is running inside a kvm VM. The card claims to be a VMware GPU.  It is being run over x2go remote desktop.   This is how my main desktop works.  All other programs, including chromium browser, run as expected.

---

### Post by Yellow Pasque on 2018-08-15
> glxinfo -B does show llvmpipe on my slow firefox system. It is running inside a kvm VM

If this is a help request, please start a new thread. Running inside a VMWare or qemu/kvm VM, you would expect to see llvmpipe.

---

### Post by luvuntu on 2018-08-17
Thanks Guys, 

actually i don't think its gonna be necessary for me to install those drivers yet, since i wont be doing any heavy video editing. 
I am gonna use this laptop mainly for Blender and other 3D Designing software. I am guessing that wont be a problem since blender is running fine.

Also i am totally new to Linux and want to keep it simple.

@TheFu
I have read those links you posted, and it said its okay and recommend me to install those AMD drivers. 
But i wont be doing that, because i think i might mess it up. And i don't want to take that risk.

But thanks for the help anyway.

---

