---
title: "Installing experimental kernel on Intrepid?"
date: 2008-12-29
forum: Hardware
---

### Post by ScottMinster on 2008-12-29
My laptop is affected by [https://bugs.launchpad.net/bugs/272247](https://bugs.launchpad.net/bugs/272247).  It was recently posted there that kernel 2.6.28 may have fixed the issue.  I tried to test it by downloading linux-image-2.6.28-4-generic from [http://packages.ubuntu.com/jaunty/linux-image-2.6.28-4-generic](http://packages.ubuntu.com/jaunty/linux-image-2.6.28-4-generic).  However, it would not cleanly install because of a problem with DKMS in the post-install:

```

 * Running DKMS auto installation service for kernel 2.6.28-4                                            
 *  nvidia (177.80)...
nvidia (177.80): Installing module.
  Kernel source for 2.6.28-4 not installed.  Cannot install this module.

```

I tried installing a couple of other related packages, linux-headers-2.6.28-4 and linux-restricted-modules-2.6.28-4, but still had problems with the nvidia DKMS.  I also tried installing linux-headers-2.6.28-4-generic, but that required a newer version of libc than I have on Intrepid.  I also tried forcing the installation (with dpkg --force-depends).  That worked, but didn't solve the DKMS problem either.

Does anyone know how I would go about installing this kernel to test it?  Is there a HOWTO somewhere that would help?

Thanks!

---

### Post by iponeverything on 2008-12-29
Adding:

```
hpet=disable
```

To your kernel options should solve your problem with no known side effects and won't require the kernel upgrade.

---

### Post by ScottMinster on 2008-12-29
I have used hpet=disable to get the 2.6.27 kernel working.  Well, mostly working -- that doesn't solve the suspend/resume problem, so I'm actually using the 2.6.24 kernel from Hardy.  I just wanted to test the new kernel to see if/how well it worked.

---

