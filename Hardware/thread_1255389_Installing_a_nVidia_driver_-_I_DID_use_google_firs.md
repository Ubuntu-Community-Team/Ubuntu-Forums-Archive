---
title: "Installing a nVidia driver - I DID use google first"
date: 2009-09-01
forum: Hardware
---

### Post by Andrés Baldrich on 2009-09-01
Hi,
I tried to install compiz on my laptop but I needed the nVidia Controller first.
So I downloaded it, closed the gui and ran the nVidia installer as root from runlvel 1
Everything went fine, but i typoed to runlevel 6 in staid of 5. When it reloaded the mozilla icon near the System menu had a cool animation, and windows were casted into the desktop from outside, and shrinked a little when closed.

But then I was in the desktop menu, under visual effects I wanted to select "extra· and it popped up that I didnt have the right controller. It asked if I wanted to install the default ones and I clicked yes.

Obviously everything came back to zero, so I tried to reinstall the nVidia driver I had downloaded from the official nVidia site. Everything was doing relatively fine during the installation and every file was successfully copied. Then it said "Searching for conflicting X files" and the bar started to load. Arroung 30% I had this error 3 times:
```
Error: Unable to open '/usr/lib/nvidia/libxgl.so.xserver-sorg-core' for reading (no such file or directory)
```I googled this error with 0 results

As I started the GUI I had this error:
(copied from log)
```
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) NVIDIA(0):     system's kernel log for additional error messages and
(EE) NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```The NVIDIA README says
> Q. My X server fails to start, and my X log file contains the error:
   
   (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
   
   
A. The X driver will abort with this error message if the NVIDIA kernel module
   fails to load. If you receive this error, you should check the output of
   `dmesg` for kernel error messages and/or attempt to load the kernel module
   explicitly with `modprobe nvidia`. If unresolved symbols are reported, then
   the kernel module was most likely built against a Linux kernel source tree
   (or kernel headers) for a kernel revision or configuration that doesn't
   match the running kernel.

   You can specify the location of the kernel source tree (or headers) when
   you install the NVIDIA driver using the --kernel-source-path command line
   option (see `sh NVIDIA-Linux-x86-185.18.36-pkg1.run --advanced-options` for
   details).

   Old versions of the module-init-tools include `modprobe` binaries that
   report an error when instructed to load a module that's already loaded into
   the kernel. Please upgrade your module-init-tools if you receive an error
   message to this effect.

   The X server reads '/proc/sys/kernel/modprobe' to determine the path to the
   `modprobe` utility and falls back to '/sbin/modprobe' if the file doesn't
   exist. Please make sure that this path is valid and refers to a `modprobe`
   binary compatible with the Linux kernel running on your system.I searched a lot of forums, reinstalled over 5 times, an it is not working. I dont know what to do (im in my first year of compuer science and had never used linux before. Only yesterday I discovered the existance of something called "run levels" and spent 30 minutes figuring out how to change them. I would happily check the kernel logs if i knew where to find them).

So.. what do you think I should do?

Edit:
I tried the modprobe command, which was further explained in another forum with the following disappointing result:
> andres@andres-laptop:~$ modprobe nvidia
andres@andres-laptop:~$ 



---

### Post by countryjake on 2009-09-01
is this a fresh install of ubuntu? if so why not try to do a fresh install and instead use the hardware drivers list under system to install the driver.
furthermore, it is best to install the graphics driver at run level 3 instead of 1 and why did you go to run level 6 instead of 5?

---

