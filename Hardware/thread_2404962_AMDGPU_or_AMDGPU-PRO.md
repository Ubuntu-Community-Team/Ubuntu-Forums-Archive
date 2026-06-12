---
title: "AMDGPU or AMDGPU-PRO?"
date: 2018-10-30
forum: Hardware
---

### Post by gottaslay on 2018-10-30
As the title says. Which one is better in terms of performance?

---

### Post by dmbomer on 2018-11-08
Not sure open source works for me.  As for pro I keep getting screen flickering and tearing.  I am unable to resolve it under 18.04.  Had no issues using it in 16.04.

---

### Post by QIII on 2018-11-08
It depends on what you mean by performance.

Scientific computing using the GPU?  AMDGPU-PRO.

AMDGPU, the open source component, was developed by AMD in concert with the Linux community -- specifically with Canonical.  It was developed and tested on Ubuntu.

AMDGPU-PRO is a proprietary overlay on top of AMDGPU that provides some high-end features. 

The vast majority of users simply do not need it.

As for the "screen flicker", that appears to be an 18.04 thing.  I encounter it *only* as a bit of artifacting when my panels auto-hide on Kubuntu.  I haven't gotten to the bottom of that yet.  Otherwise, I have encountered no problems.

You can get a bit better performance with AMDGPU by adding /etc/X11/xorg.conf.d/20-amdgpu.conf containing the following:

```
Section "Device"
    Identifier "Your Device Here"
    Driver "amdgpu"
    Option "AccelMethod" "glamor"
    Option "TearFree" "true"
EndSection
```

Some people add the option for DRI 3, but that is already enabled by default with AMDGPU now.

The big takeaway here is this:  AMDGPU and AMDGPU-PRO are not two different drivers.  They are the basic driver and an an additional overlay.

---

