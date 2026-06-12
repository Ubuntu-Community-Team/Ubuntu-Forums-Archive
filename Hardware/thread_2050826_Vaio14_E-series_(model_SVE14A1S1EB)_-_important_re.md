---
title: "Vaio14 E-series (model SVE14A1S1EB) - important re power consumption"
date: 2012-08-31
forum: Hardware
---

### Post by Vidar30 on 2012-08-31
Finally my Vaio laptop use less power than running on Win7!

I experienced a drop down in power usage to less than 10 watt by doing the following:

- First I followed these instructions to uninstall properiatary video ATI driver:
[http://nerdysermons.blogspot.no/2011/11/solve-graphic-driver-errors-unity-3d.html](http://nerdysermons.blogspot.no/2011/11/solve-graphic-driver-errors-unity-3d.html)

- Secondly I disabled Radeon discrete graphics by adding "echo OFF > /sys/kernel/debug/vgaswitcheroo/switch" to /etc/rc.local as described here:
[http://blog.ejbca.org/2012/02/ubuntu-gnulinux-1204-precise-on-sony.html](http://blog.ejbca.org/2012/02/ubuntu-gnulinux-1204-precise-on-sony.html)

I'm running Jupiter and now my laptop use less than 10W (6-7W), in contrast to >20W as it did before I executed those small steps mentioned above. Quite some difference! Until now, I've never managed to make my Vaio laptop be energy efficient.

How do I rapport this to Canonical?
(for this model of laptop this config should be made default)

---

