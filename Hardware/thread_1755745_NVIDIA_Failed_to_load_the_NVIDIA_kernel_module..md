---
title: "NVIDIA: Failed to load the NVIDIA kernel module."
date: 2011-05-11
forum: Hardware
---

### Post by HughJarse on 2011-05-11
I get this error on boot up
```
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.
```

---

### Post by HughJarse on 2011-06-02
Is this the wrong forum for this question?

---

### Post by HughJarse on 2011-06-05
This problem went away after a recent update. Oh well, at least it's fixed.

---

### Post by levymichel on 2011-06-07
> **HughJarse said:**
> I get this error on boot up
```
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.
```

I have exactly the same problem arriving with the last update of 
ubuntu 10.04LTS with the last kernel 2.6.32-33.
So I choose by default to use the kernel 2.6.32-32.
I have tried to reinstall the nvidia driver without any success.
What is the solution ? Wait the next update ?

---

### Post by Dlambert on 2011-06-07
In my experience, i would have to install driver twice.

---

