---
title: "Different settings for different pointer devices?"
date: 2009-04-13
forum: Hardware
---

### Post by Peasantoid on 2009-04-13
I have a number of different pointer devices (trackpad, mouse, tablet) connected to my computer. The problem is that having optimal settings for one makes the rest totally unusable:

* Optimal trackpad = superfast mouse, slow tablet
* Optimal mouse = slow trackpad, slow tablet
* Optimal tablet = superfast trackpad, superfast mouse

How do I establish different settings "profiles" for each device? I'd dive into xorg.conf, but I have no idea of the ins and outs involved in doing so.

[edit] Never mind. Involves setting the options "MinSpeed", "MaxSpeed", and "AccelFactor".

---

