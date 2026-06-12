---
title: "Kernel 3.2.0 and nvidia 173.14.30"
date: 2012-04-19
forum: Hardware
---

### Post by ropetili on 2012-04-19
Use a Nvidia FX5500. Functional driver for it is 173. But X.org and kernel does not come to terms with it all. I can guide you can use the Nvidia proprietary driver on Ubuntu 4.12?

---

### Post by kc1di on 2012-04-19
> **ropetili said:**
> Use a Nvidia FX5500. Functional driver for it is 173. But X.org and kernel does not come to terms with it all. I can guide you can use the Nvidia proprietary driver on Ubuntu 4.12?

Not sure I understand your Question but here goes. 
I'm assuming that 4.12 is a typo and you mean 12.04.  4.12 is very old.  The 173 driver should work fine and if your in ubuntu 12.04 should be install able via system settings >Additional drivers tool.

If that should not work for you it can be install via download from Nvidia but that's a little more involved.

---

### Post by ropetili on 2012-04-19
Oh,yes. With 4.12 is wrong. In the Additional Drivers driver tells me there for my configuration. And the installation of the Software Center gives me the error:
```
nvidia-173: Depends: x11-common (>= 1:7.0.0) dar versiunea 1:7.6+12ubuntu1 este pe cale de a fi instalat&#259;
            Depends: xorg-video-abi-10 dar nu este pe cale de a fi instalat
            Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) dar versiunea 2:1.11.4-0ubuntu10 este pe cale de a fi instalat&#259;

```
(My system is in Romanian)
How to solve?

---

### Post by kc1di on 2012-04-19
it seems that this is a known bug and they will be working on it.
See 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053")
This comment is found on the bug pages:

> We do anticipate getting one more -nvidia release prior to Precise shipping, and hope that will include an updated -173. Maybe we'll get -96 too but hard to say; that appears to get attention less frequently, so we might have to drop it.

In any case, I think we should wait on dropping these until closer to final freeze, so we can see what NVIDIA puts out.

Is it possible for us to toggle off -173 and -96 from being shown in jockey until we think it'll work? Might help quell some of the bug reports we get

Sorry it does not look like it's going to happen right now :(

---

### Post by ropetili on 2012-04-19
Ok. Now I understand.

---

