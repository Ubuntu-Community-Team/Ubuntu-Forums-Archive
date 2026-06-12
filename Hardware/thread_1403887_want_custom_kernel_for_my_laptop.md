---
title: "want custom kernel for my laptop"
date: 2010-02-10
forum: Hardware
---

### Post by SaintDanBert on 2010-02-10
I have a Thinkpad laptop and I'm currently running the generic -- shipped with the distro or update download -- kernel. [color=blue]How do I config and build a kernel that is optimal for my laptop?[/color]

What do I mean by "optimal for my laptop?"
[list]
[*] remove things that do not apply to my hardware
[*] enable features supported by my hardware
[*] disable features un-needed by my applications
[*] enable features required by my applications
[*] low fat
[*] high octane
[/list]

If someone has a custom kernel config for a Core Two Duo processor Thinkpad, I'd love to see what you are running.

My sysinfo reports the following:
```

        GenuineIntel, Intel(R) Core(TM)2 Duo CPU     L7500  @ 1.60GHz
        Number of CPUs: 2
        CPU clock currently at 800.000 MHz with 4096 KB cache
        Numbering: family(6) model(15) stepping(11)
        Bogomips: 3192.30

        Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge
        mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht 
        tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64
        monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida
        tpr_shadow vnmi flexpriority

```

The generic kernels are all 32-bit not 64-bit. I'd like to move up, but I hear there is grief with 64-bit versus several applications.

---

### Post by Revolutionary101 on 2010-02-10
Here is a tutorial on how to make and install your own custom kernel.

[http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html")

To get the kernel go to [http://www.kernel.org/](http://www.kernel.org/)

Just post to the thread if you need any help with compiling. I just have to tell you that you might not see that much of a difference in speed by compiling your own kernel. Although it is a good educational experience for any Linux user wanting to learn about how Linux works.

As for the 32 bit and 64 bit problem I don't know how to fix that. You may be able to change the kernel to 64 bit when you are customizing the kernel.

---

### Post by falconindy on 2010-02-10
Running a 64-bit kernel on a 32-bit userland is **possible**, but not for the faint of heart. You're better off reinstalling.

Recompiling a kernel can change performance dramatically. I say change and not improve, because there's always room for error and it depends what you decide to patch in on your own (if anything). My recent kernels have been built with the [-ck patchset](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/) which I'm really digging.

I was always a fan of using the Canonical patched source for recompiling kernels on Ubuntu. [This blog](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/) served me as an excellent reference.

---

