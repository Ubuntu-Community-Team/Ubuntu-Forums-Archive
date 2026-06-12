---
title: "X crashes after plugging in external display"
date: 2010-11-19
forum: Hardware
---

### Post by f.zweig on 2010-11-19
Hey! I'm having a rather strange problem:

I'm running an bottom-up installation of Maverick with the nouveau driver on an GeForce 8400M GS. When I'm plugging in an external display (via HDMI), X.org crashes, throwing me back to GDM running a smaller resolution and the mirrored image on both displays.

After changing the resolution of one of the displays or disabling one via gnome-display-properties (which uses randr AFAIK), X crashes again. The same happens on every user account.

The strange thing is that I can't reproduce it with a live system. So, I'd like to track down what the problem is, to fix it or file a bug eventually.

My Xorg.0.log doesn't show any relevant information, and kern.log only has

```
[drm:output_poll_execute] *ERROR* delayed enqueue failed -125
```

Is anybody able to give me a few hints how to get a proper error message? Thank you!

---

### Post by f.zweig on 2010-11-21
Just to be clear: I'm not asking for any solution, I'm asking for tips how to get a proper error log the examine it myself first. No ideas?

---

