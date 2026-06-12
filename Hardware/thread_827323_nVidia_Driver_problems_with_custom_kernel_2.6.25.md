---
title: "nVidia Driver problems with custom kernel 2.6.25"
date: 2008-06-12
forum: Hardware
---

### Post by fieldstone on 2008-06-12
Okay, I've already found a workaround for this problem, but I'm wondering if anyone knows what's going on and can tell me how to fix it.

With the stock Ubuntu kernel, my video works just fine, but my machine freezes when on battery and I can't control my backlight, so I custom compiled a 2.6.25.6 kernel. No problem so far, right?

But... the current nVidia drivers (169.12, 173.14.05, all the ones in between - seemingly all the ones with PowerMizer) have very choppy video; unwatchable, really.

The open-source (nv) nVidia driver works fine, but obviously it has no GL acceleration. I resolved the problem for now by installing the latest legacy version (96.43.05), but I'd much rather have a newer driver version if I can.

So my question is this: does anyone know of some incompatibility between the recent non-legacy nVidia drivers and kernel 2.6.25?

Is there some way to fix it myself, or is it already a known issue that's going to be fixed in a future kernel or nVidia driver release?

(Bueller? ... Bueller?)

---

