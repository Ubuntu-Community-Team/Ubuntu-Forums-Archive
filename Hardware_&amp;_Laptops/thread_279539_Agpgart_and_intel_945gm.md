---
title: "Agpgart and intel 945gm"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by JaRoLLz on 2006-10-18
Dear all,

I've downloaded both these packages from intel.

IEGD_5_1_Linux.tgz
Intel-3.4.3006-20051209.i386.tar.gz

It is said in the website that these packages are for intel 945gm graphics chipset with linux os.

The first problem is, I don't understand at all (](*,) ) about how to install this driver.

The second problem is, I happen to try to install a wrong driver (i915) and the terminal said that AGPGART module is not compiled and Kernel is not compiled or something like that. Please help me...

---

### Post by tsberry901 on 2006-10-19
Recompile your module. You need the source files.

---

### Post by ctnd on 2007-01-27
> **tsberry901 said:**
> Recompile your module. You need the source files.

Hello. I have the same problem:

```
cin@chrislaptop:~/Desktop$ wget http://downloadmirror.intel.com/df-support/8211/eng/dri-I915-v1.1-20041217.i386.rpm
--01:27:49--  http://downloadmirror.intel.com/df-support/8211/eng/dri-I915-v1.1-20041217.i386.rpm
           => `dri-I915-v1.1-20041217.i386.rpm.1'
Resolving downloadmirror.intel.com... 193.38.108.206, 193.38.108.214
Connecting to downloadmirror.intel.com|193.38.108.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,755,767 (2.6M) [application/octet-stream]
 
100%[====================================>] 2,755,767    477.91K/s    ETA 00:00
 
01:27:55 (475.44 KB/s) - `dri-I915-v1.1-20041217.i386.rpm.1' saved [2755767/2755767]
 
cin@chrislaptop:~/Desktop$ sudo alien dri-I915-v1.1-20041217.i386.rpm --scripts
dri-i915_v1.1-20041218_i386.deb generated
cin@chrislaptop:~/Desktop$ sudo dpkg -i dri-i915_v1.1-20041218_i386.deb
(Reading database ... 112666 files and directories currently installed.)
Preparing to replace dri-i915 v1.1-20041218 (using dri-i915_v1.1-20041218_i386.deb) ...
Unpacking replacement dri-i915 ...
Setting up dri-i915 (v1.1-20041218) ...
 
 
ERROR: AGPGART module did not compile
 
 
ERROR: AGPGART module did not compile - AGP module turned off in kernel ??
 
 
ERROR: Kernel modules did not compile
cp: cannot stat `drm/i915.ko': No such file or directory
Failed to install file /lib/modules/2.6.15-27-386/kernel/drivers/char/drm/i915.ko
cp: cannot stat `agpgart-2.0/intel-agp.ko': No such file or directory
Failed to install file /lib/modules/2.6.15-27-386/kernel/drivers/char/agp/intel-agp.ko
The installation of one or more files failed
 
You will need to reboot for the changes to take effect,
as we were unable to unload the current kernel modules.
```

I have no idea how to debug this problem. Where can I get these source files you speak of? Or better yet, is there a HOWTO on the forum about how to install the correct drivers for Intel 915GM/GMS/910GML? (I have been unable to find one.)

---

