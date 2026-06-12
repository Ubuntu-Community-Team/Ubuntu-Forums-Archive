---
title: "Need basic help with graphics card"
date: 2011-04-29
forum: Hardware
---

### Post by blukid on 2011-04-29
Hi, I've got 10.10 installed on a Dell Dimension 4600c which has an integrated Intel Extreme Graphics 2 video card. It's working well, but I want to try the proprietary driver to see if I can get better performance with games. If I'm correct, [COLOR=Red][here]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=8203&ProdId=1044&lang=eng")[/COLOR] is the link to the linux driver.

 Is this the correct driver? Is there anything else I need? And how would I install it? Sorry if too many questions in one post, never installed a graphics driver before.

---

### Post by dabl on 2011-04-29
I doubt seriously you want to play with that old 2004 driver from Intel -- if you are presently running the xserver-xorg-video-intel driver in 10.10, then you already have the latest and greatest.

What exactly is your GPU model -- can you run ```
lspci -v
``` in a terminal window, and paste in just the VGA stanza of the output?

---

### Post by blukid on 2011-04-29
thanks for the reply. Here's the output:
```

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0154
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ed98 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```
how would i check which driver i'm currently using?

Thanks.

---

### Post by dabl on 2011-04-29
Here is Ubuntu's guidance on video drivers:  [https://help.ubuntu.com/community/RestrictedDrivers](https://help.ubuntu.com/community/RestrictedDrivers)

As you can see, xserver-xorg-video-intel is the latest driver for Intel GPUs.

```
lsmod | grep intel
``` will show you all kernel modules with the term "intel" in them.  For video, you might see something like

```
intel_agp
```

If you have desktop effects enabled, you might try disabling them, to improve performance of games.

---

### Post by blukid on 2011-04-30
Ok thanks a lot for all your help :)

---

