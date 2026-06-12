---
title: "/usr/lib/dri/r600_dri.so not found"
date: 2009-12-02
forum: Hardware
---

### Post by ndyguy on 2009-12-02
Today I started getting an error message at every startup stating the following:

```
(EE) AIGLX error: dlopen of /usr/lib/dri/r600_dri.so failed
(/usr/lib/dri/r600_dri.so: cannot open shared object file: No such file or
directory)
(EE) AIGLX: reverting to software rendering
```

If on the next window I select something like revert to software rendering it eventually loads.  Why did this start happening and better yet, how do I fix it?

I'm using an AMD Turion X2 64-bit with Kubuntu 9.10.  Last night I got about a week's worth of updates, including the 2.6.31-15 kernel, but didn't notice the problem until just now.  If logs or copies of files would be helpful please show me the file path or explain how to get them.

Thanks in advance.

---

### Post by Francesco Ricci on 2009-12-02
I have the same problem.
 
I have Kubuntu 9.10 and today i have installed the new kernel and the new XORG update.
 
My computer is a HP Pavilion dv5 with a Radeon.
 
There isn't any file /usr/lib/dri/r600_dri.so on my system.
 
Can someone help us?

---

### Post by sspr on 2009-12-03
Confirmed here too. Boot stability is very bad. This is most likely a serious regression due to the upgrade of the xserver-xorg-video-all package

We need to submit a bug report asap.

Edit:
The bug was submitted as [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483)
See there for all information

---

### Post by Yellow Pasque on 2009-12-03
> (EE) AIGLX error: dlopen of /usr/lib/dri/r600_dri.so failed

This isn't anything to worry about. The r600_dri.so file is found in mesa-dri package, but Ubuntu does not ship this file with their Mesa because the Ubuntu Karmic kernel does not have the necessary DRM bits to support open-source 3D on RadeonHD cards.

---

### Post by ndyguy on 2009-12-11
Once again performed a bunch of updates, including a new kernel update, and the problem has been fixed.  Thanks for all help and information.

---

### Post by Francesco Ricci on 2009-12-12
Do you means kernel 2.6.31.16.29?

---

