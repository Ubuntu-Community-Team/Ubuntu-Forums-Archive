---
title: "Unity 2D is faster in a VM than on real hardware. What gives?"
date: 2012-08-06
forum: Hardware
---

### Post by Gullible Jones on 2012-08-06
I have tried Ubuntu 12.04 on my Eee 1005HAB netbook. It is usable on that machine, but not fast, nor pleasant to use. The usual stuff - menus lag, windows resize jerkily, the Unity launcher takes several seconds to pop up, applications take a long time to start... Both in Unity 2D and 3D. Also notable in Unity 2D is the extremely sluggish scaling of the Unity 2D desktop switcher.

Today I got to try out 12.04 under QEMU-KVM, running on top of a Dell Precision 390 workstation. Lo and behold, it *flew* - there is no sluggishness to the Unity 2D interface at all.

Granted, the Dell is a powerful computer, and KVM has full access to its CPU and to 1 GB of its main RAM... But this is still weird, because the emulated video card is a Cirrus CLGD 5446, with only 4 MB of video RAM. And effects that lag like mad with fully accelerated Intel graphics, work absolutely fine with barely accelerated, emulated Cirrus graphics and next to no video RAM.

What's going on here? Is the intel driver that bad in 12.04? Or is KVM doing something to make the puny emulated hardware beefier?

---

### Post by Mikeb85 on 2012-08-06
> **Gullible Jones said:**
> I have tried Ubuntu 12.04 on my Eee 1005HAB netbook. It is usable on that machine, but not fast, nor pleasant to use. The usual stuff - menus lag, windows resize jerkily, the Unity launcher takes several seconds to pop up, applications take a long time to start... Both in Unity 2D and 3D. Also notable in Unity 2D is the extremely sluggish scaling of the Unity 2D desktop switcher.

Today I got to try out 12.04 under QEMU-KVM, running on top of a Dell Precision 390 workstation. Lo and behold, it *flew* - there is no sluggishness to the Unity 2D interface at all.

Granted, the Dell is a powerful computer, and KVM has full access to its CPU and to 1 GB of its main RAM... But this is still weird, because the emulated video card is a Cirrus CLGD 5446, with only 4 MB of video RAM. And effects that lag like mad with fully accelerated Intel graphics, work absolutely fine with barely accelerated, emulated Cirrus graphics and next to no video RAM.

What's going on here? Is the intel driver that bad in 12.04? Or is KVM doing something to make the puny emulated hardware beefier?

Netbooks are simply that bad.  Hence why they're all getting replaced with tablets and Ultrabooks...  

Plus Unity 2D doesn't require much hardware acceleration, so access to that workstation CPU enables it to fly.

---

