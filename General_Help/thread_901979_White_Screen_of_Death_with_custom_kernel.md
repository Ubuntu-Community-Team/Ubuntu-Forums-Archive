---
title: "White Screen of Death with custom kernel"
date: 2008-08-26
forum: General Help
---

### Post by LegoAddict on 2008-08-26
So I was running 2.6.24 on my desktop quite happily until I saw Tux On Ice, something which promised to fix the suspend/resume problem that dogs mine and many Linux systems.  So I followed the How To here : [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) , and I got no error messages.  Every thing went perfectly.  But when I booted it I got in and logged in, and I just got a white screen which I was able to rotate on the desktop cube, but that's all.  My old kernel was a little rocked too and it took me a little bit to get it working again.

The kernel I compiled was the newest available kernel on kernel.org (2.6.26).  I am on a 32 bit Intel system, any other hardware is available upon request...

I am running Ubuntu 8.04.  Should I try recompiling the kernel with 2.6.24, or what?

---

### Post by LateNiteTV on 2008-08-26
> **LegoAddict said:**
> So I was running 2.6.24 on my desktop quite happily until I saw Tux On Ice, something which promised to fix the suspend/resume problem that dogs mine and many Linux systems.  So I followed the How To here : [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) , and I got no error messages.  Every thing went perfectly.  But when I booted it I got in and logged in, and I just got a white screen which I was able to rotate on the desktop cube, but that's all.  My old kernel was a little rocked too and it took me a little bit to get it working again.

The kernel I compiled was the newest available kernel on kernel.org (2.6.26).  I am on a 32 bit Intel system, any other hardware is available upon request...

I am running Ubuntu 8.04.  Should I try recompiling the kernel with 2.6.24, or what?

post all hardware specs along with your kernel config.

<snip language>
im just going to make a nice little comment here: i use freebsd, not linux... ever.
the freebsd way of completely updating/patching your system and compiling a custom kernel:

```
cvsup /standard-supfile
cd /usr/src; mergemaster -p
make buildworld
make buildkernel KERNCONF=WHATEVER
make installkernel KERNCONF=WHATEVER
make installworld
mergemaster
reboot
```

---

### Post by LegoAddict on 2008-08-28
Processor:  2 3ghz Intel Pentium D processors
Memory:  1 GB
Present (stable) kernel: Linux 2.6.24-19 Generic (default Ubuntu via Update)
Desired kernel:  2.6.26.3 with TuxOnIce latest patch installed
Available diskspace: 8.4 GB
Graphics Card: ATI RV370
Sound Card:  82801G (ICH7 Family) High Definition Audio Controller
Motherboard:  ASUS P5LD2
American Megatrends BIOS 

Hope this provides enough info.

---

### Post by sdennie on 2008-08-28
> **LateNiteTV said:**
> 
the freebsd way of completely updating/patching your system and compiling a custom kernel:

```
cvsup /standard-supfile
cd /usr/src; mergemaster -p
make buildworld
make buildkernel KERNCONF=WHATEVER
make installkernel KERNCONF=WHATEVER
make installworld
mergemaster
reboot
```

As opposed to:
```

tar xvf linux-VERSION.tar.bz
cd linux-VERSION
make menuconfig
fakeroot make-kpkg --initrd --append-to-version=-$1 kernel_image kernel_headers
sudo dpkg -i ../linux*VERSION*.deb

```

The Debian/Ubuntu way...

> **LegoAddict said:**
> Processor:  2 3ghz Intel Pentium D processors
Memory:  1 GB
Present (stable) kernel: Linux 2.6.24-19 Generic (default Ubuntu via Update)
Desired kernel:  2.6.26.3 with TuxOnIce latest patch installed
Available diskspace: 8.4 GB
Graphics Card: ATI RV370
Sound Card:  82801G (ICH7 Family) High Definition Audio Controller
Motherboard:  ASUS P5LD2
American Megatrends BIOS 

Hope this provides enough info.

This symptom sounds like you are using compiz without OpenGL or proper drivers.  It's probably the latter as when you build a custom kernel, you will need to install drivers for NVIDA and most (all?) ATI cards for that specific kernel.  I'm not familiar with ATI so can't recommend a guide but, you should be able to find one via google or maybe someone can recommend one.

---

### Post by LegoAddict on 2008-08-31
Ok.  I'll look into that.  Also, it seems that no drivers are installed; sound no longer works as well.  But we'll fix that when we can run the system ;)

---

### Post by sdennie on 2008-08-31
> **LegoAddict said:**
> Ok.  I'll look into that.  Also, it seems that no drivers are installed; sound no longer works as well.  But we'll fix that when we can run the system ;)

The sound issue is likely because you are using hda_intel for sound and, if you used the Ubuntu kernel config as your base, it doesn't have that module enabled by default (nor iwl3945 I don't think).  You can probably fix it by just downloading the latest ALSA, building and installing it.

---

### Post by LegoAddict on 2008-09-05
I think I've pinpointed the real problem:  I tried to install a windows internet driver via ndiswrapper, which installed and worked great under the original kernel, and ndiswrapper said it could not detect hardware, so possibly Ubuntu has lost the ability to detect my hardware...

---

