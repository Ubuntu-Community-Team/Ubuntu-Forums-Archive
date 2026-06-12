---
title: "Virtualization"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by sasanf on 2007-07-06
I hope this is the right forum to post the following?  I have a Dell Inspiron 6400 that supports hardware virtualization.  It has an Intel Core Duo processor in it.  I have update to the latest BIOS from Dell (A17).  I can't get the command sudo modprobe kvm-intel to do anything.  Every time I run it, I am returned to the blank command line.  I have been following the tutorial located at [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM).  Below is the output when I run the command grep -E ‘^flags.*(vmx|svm)’ /proc/cpuinfo.  When I copy and paste the command nothing is returned but when I manually type the command in data is returned.

superman@superman-laptop:~$ grep -E '^flags.*(vmx|svm)' /proc/cpuinfo
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr

I almost forgot.  I have enabled virtualization in the BIOS.  I have rwx permissions on /dev/kvm.

---

### Post by dreadlord_chris on 2007-07-06
if I'm not mistaken **modprobe** will only output something if there's either an error or if passed a **-v (verbose)**.
from modprobe man pages:
> 
-v --verbose
              Print messages about what the program is doing.  Usually modprobe only prints mes&#8208;
              sages if something goes wrong.


If there is no output it generally means that the commmand was sucessful.
Also, your *grep* output shows that the **vmx** extensions are present for your CPUs

---

### Post by sasanf on 2007-07-06
> **dreadlord_chris said:**
> if I'm not mistaken **modprobe** will only output something if there's either an error or if passed a **-v (verbose)**.
from modprobe man pages:


If there is no output it generally means that the commmand was sucessful.
Also, your *grep* output shows that the **vmx** extensions are present for your CPUs

The following is the output with the -v tag:

insmod /lib/modules/2.6.20-16-generic/kernel/drivers/kvm/kvm.ko 
insmod /lib/modules/2.6.20-16-generic/kernel/drivers/kvm/kvm-intel.ko 

Does this mean that the modules have been installed?

---

### Post by dreadlord_chris on 2007-07-06
> **sasanf said:**
> The following is the output with the -v tag:

insmod /lib/modules/2.6.20-16-generic/kernel/drivers/kvm/kvm.ko 
insmod /lib/modules/2.6.20-16-generic/kernel/drivers/kvm/kvm-intel.ko 

Does this mean that the modules have been installed?

yup.... sure does...

---

### Post by sasanf on 2007-07-06
Thanks for the help.  Now if I can figure out how to use kvm with qemu launcher.  I don't need to install kqemu since my proc support virtu.  Anyway, I suppose this problem is for a thread on the qemu launcher forum... if there is one.

---

