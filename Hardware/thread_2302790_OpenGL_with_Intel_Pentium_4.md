---
title: "OpenGL with Intel Pentium 4"
date: 2015-11-13
forum: Hardware
---

### Post by fillip1 on 2015-11-13
On Computer with Lubuntu 15.10 is not working OpenGL.
~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
intel_do_flush_locked failed: Input/output error

I have only integrtae GPU Intel 82865g on Pentium 4.

-OpenGL-
Vendor        : Intel Open Source Technology Center
Renderer        : Mesa DRI Intel(R) 865G x86/MMX/SSE2
Version        : 1.3 Mesa 11.0.2
Direct Rendering        : Yes

-Version-
Kernel        : Linux 4.2.0-16-generic (i686)
Distribution        : Ubuntu 15.10
-Current Session-
Desktop Environment        : LXDE

---

### Post by grahammechanical on 2015-11-13
I would say that what you are seeing is the limitation of the GPU. The Mesa 11.0.2 driver was released September 28 2015. So, Lubuntu 15.10 has done well in giving you the latest Mesa driver.

[http://www.mesa3d.org/](http://www.mesa3d.org/)

This command will give more information about the OpenGL driver

```
glxinfo | grep OpenGL
```

Regards.

---

### Post by Yellow Pasque on 2015-11-13
> I would say that what you are seeing is the limitation of the GPU.
glxgears shouldn't be crashing regardless of what GPU is used. I would look at dmesg or /var/log/Xorg.0.log for more clues on the crash.

---

### Post by fillip1 on 2015-11-13
glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) 865G x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 11.0.2
OpenGL extensions:

---

### Post by fillip1 on 2015-11-13
dmesg: [http://paste.ubuntu.com/13250362/](http://paste.ubuntu.com/13250362/)
Xorg.0.log [http://paste.ubuntu.com/13250366/](http://paste.ubuntu.com/13250366/)

---

### Post by mikewhatever on 2015-11-13
You can't expect OpenGL to work well on a Pentium 4 era GPUs in general.

---

### Post by fillip1 on 2015-11-13
I don't nedd to work well. Just work some how. For example now i can't use Charts in LibeOffice, it always crash (and i think it's because of OpenGL).
In past (aprox.2 years ago) I used these Pentium without errors.

---

### Post by blm-ubunet on 2015-11-13
Your xorg log shows:
59.814] (EE) intel(0): Detected a hung GPU, disabling acceleration.

Could try to disable SNA acceleration..
file /etc/X11/xorg.conf
```
Section "Device"
        Identifier "intel"
        Driver "intel"
        Option "AccelMethod" "UXA"
EndSection
```

What's all this stuff in your grub boot options about ?
"drm.debug=0xe plymouth:debug=1=1"

The last bit looks suspect..

---

### Post by Yellow Pasque on 2015-11-13
I would try the latest upstream kernel (4.3.x). [https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels_.28manually.29](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels_.28manually.29)
If that doesn't work, consider following the advice on bug reporting:
```
[   59.809634] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
[   59.809637] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
[   59.809640] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
[   59.809643] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
[   59.809646] [drm] GPU crash dump saved to /sys/class/drm/card0/error
```

---

### Post by mikewhatever on 2015-11-14
> **fillip1 said:**
> I don't nedd to work well. Just work some how. For example now i can't use Charts in LibeOffice, it always crash (and i think it's because of OpenGL).
In past (aprox.2 years ago) I used these Pentium without errors.

Well, if you know that an older release like 14.04 works better, use it. LibreOffice has been planning to integrate hardware acceleration for some years, but, once again, an over a decade old GPU is unlikely to be the target for new features. Usually, really old hardware is just blacklisted.

---

### Post by fillip1 on 2015-11-15
I don't know anything about GRUB options.
Your advice is Remove row "drm.debug=0xe plymouth:debug=1=1"?

---

### Post by blm-ubunet on 2015-11-15
I would do just one change at a time & test.
Your Xorg.0.log & glxgears helpfully reveals problems..

First I would disable "SNA" acceleration reboot/test.
Then try remove/modify grub boot cmd options.
A internet search on those grub cmd options should reveal what they are/were for..
Old cruft ??

---

### Post by fillip1 on 2015-11-16
Solved by disabling SNA acceleration. [http://ubuntuforums.org/showthread.php?t=2182033](http://ubuntuforums.org/showthread.php?t=2182033)
Thanks

---

### Post by fillip1 on 2015-11-16
BTW: "drm.debug=0xe plymouth:debug=1=1" in GRUB is made by Xdiagnose (3.8.1)

---

### Post by blm-ubunet on 2015-11-16
Glad you're working again.
Thanks for that info, I learnt something.
One has to admit that "debug=1=1" looks like a typo. Must evaluate to true..

---

