---
title: "amdgpu driver on Radeon 200 series GPU not loading, troubleshooting"
date: 2016-12-15
forum: Hardware
---

### Post by pmb2 on 2016-12-15
Hi,

I would like to try out the amdgpu driver, especially to test its OpenCL support. I only seem to be able to use the radeon driver though. The GPU is a R290X, so I have followed some instructions on how to enable experimental support: [https://www.linkedin.com/pulse/using-newer-amdgpu-driver-ubuntu-1604lts-dennis-mungai](https://www.linkedin.com/pulse/using-newer-amdgpu-driver-ubuntu-1604lts-dennis-mungai) .

Now I have built a custom kernel with the required option:
```
fa2k@blackhole:~$ uname -a
Linux blackhole 4.8.0-30-generic #32+fafafa SMP Wed Dec 14 22:41:29 CET 2016 x86_64 x86_64 x86_64 GNU/Linux
fa2k@blackhole:~$ grep AMDGPU_CIK /boot/config-4.8.0-30-generic 
CONFIG_DRM_AMDGPU_CIK=y

```

And set the kernel command line:
```
fa2k@blackhole:~$ cat /proc/cmdline 
BOOT_IMAGE=/vmlinuz-4.8.0-30-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash amdgpu.exp_hw_support=1 vt.handoff=7

```

Still, only radeon is loaded,
```
fa2k@blackhole:~$ lsmod | grep radeon
radeon               1515520  75
i2c_algo_bit           16384  1 radeon
ttm                   102400  1 radeon
drm_kms_helper        167936  1 radeon
drm                   368640  8 radeon,ttm,drm_kms_helper
fa2k@blackhole:~$ lsmod | grep amdgpu
fa2k@blackhole:~$ 

```

Any hints on how to troubleshoot?

Thanks

---

### Post by pmb2 on 2016-12-15
Found the solution: blacklist the radeon driver. Works great (but didn't solve my original OpenCL problem)

For anyone coming across this post, there's basically 3 things to do:
1. Build a new kernel and set the configuration option in the menus (find under Device Drivers, Graphics support)
[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

2. Configure a boot parameter to enable experimental hardware support: (amdgpu.exp_hw_support=1)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

3. Blacklist the radeon module: I added another kernel boot parameter: modprobe.blacklist=radeon . May also be possible to use a file in /etc/modprobe.d, but it could be loaded too early in the boot process for that to work.

---

### Post by QIII on 2016-12-15
Hello!

I would suspect that it is necessary to install AMDGPU-PRO and the Vulkan SDK to take full advantage of OpenCL.  According to AMD, the R9 290X is supported by AMDGPU-PRO.

You can download AMDGPU-PRO [here]("http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx") and follow the instructions for installing it and the Vulkan SDK.

I wrote a short article on my experience with AMDGPU-PRO and an R9 380X running SETI@Home on BOINC [here]("http://theleftcoastgeek.net/index.php/categories/13-using-amdgpu-pro-and-the-vulkan-sdk-for-boinc-projects").  By the way, I just used the mainline 4.8 kernel in 16.04 without having to set any flags or recompile the kernel.

---

### Post by pmb2 on 2016-12-15
Thanks for the tip QIII! I tried AMDGPU-PRO but I couldn't get past the grub screen, and read it didn't support kernel 4.8, so gave up. Will definitely give it another go. There's a few more things to try, like using a different monitor, and again blacklisting radeon. (By the way, I'm after almost the same thing, to run Folding@home and generate some much needed heat;)

---

### Post by QIII on 2016-12-15
A release 4.9 mainline kernel is available.  That is supposed to take care of most of the AMDGPU-PRO loose ends.  I don't think it's on Canonical's repos just yet, though.

---

### Post by wildmanne39 on 2016-12-15
With the 4.9 kernel you'll need X.Org Server 1.19.0 and xf86-video-amdgpu 1.2.0 too at least that is what the article says.

If you get the X.org server 1.19.0 installed please post the directions, I am sure it would help many people.

---

### Post by pmb2 on 2016-12-15
AMDGPU-PRO works now :D I had to blacklist radeon (but there's probably a cleaner solution).

I misremembered about the error I got though. It successfully booted to X, but never showed the login screen and I got an error about "low graphics mode". Couldn't get past it.

Anyway, with the radeon driver disabled, and AMDGPU-PRO enabled, Folding@home worked right away! Fantastic! (With the non-PRO diver, and the paulo-miguel-dias PPA, I got a segfault, instead of a compilation error like before, which I think is an improvement. So I think the open source OpenCL implementation is also getting there, just not quite yet)

---

### Post by QIII on 2016-12-15
If you don't mind terribly, could you outline clearly exactly what you did step by step?  It would be nice if others had the solution without having to piece it together from our conversation.

Thanks!

---

### Post by pmb2 on 2016-12-15
Well yeah, good point. Just not sure if it's the best way to do it, but it works..[B] How to fix AMDGPU-PRO "low graphics mode" error:

Symptom: The computer boots, but shows a troubleshooting dialogue box instead of the login screen.[/B]

Temporary fix: add a kernel command line for just the current startup session:
Reboot, then just as the computer leaves the BIOS POST screen, spam the ctrl and arrow-down keys (or any other key). This will give you the boot menu. Go to the top menu entry, "Ubuntu" and press "e" to edit. Locate the line starting with "linux", and add the text "modprobe.blacklist=radeon" to the very end of it. Press F10 to boot. The problem should now be fixed once.



To fix permanently:
Edit file /etc/default/grub

Locate the line with GRUB_CMDLINE_LINUX_DEFAULT=

Add a space and then the text "modprobe.blacklist=radeon", almost at the  end of the line, but before the last quotation mark. It should read  something like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modprobe.blacklist=radeon"

Update grub by running "sudo update-grub"

Reboot

---

