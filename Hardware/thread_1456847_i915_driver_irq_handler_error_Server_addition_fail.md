---
title: "i915_driver_irq_handler error Server addition failing to boot"
date: 2010-04-17
forum: Hardware
---

### Post by onyxwolf on 2010-04-17
I run server 9.10 on an old dell dimension 2400. It has been working great until I had to reboot it this last time. During boot I'm getting the following 3 errors:

[ 7.402952]render error detected, EIR: 0x00000010
[ 7.402958] [drm:i915_driver_irq_handler] *ERROR* EIR stuck: 0x00000010, masking
[ 7.402966] render error detected, EIR: 0x00000010

and then nothing...

Those errors stay on screen and I can hit enter and get the cursor to drop and input stuff but nothing happens with it. If I stick a USB it comes up with lines for it to recognize the HW but nothing still after that. If I hit the ctrl+alt+del it properly resets!

Now I've found a bug report with these lines and a possible fix.

The Bug is at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404064]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404064")

and the fix is a patch at [http://lists.freedesktop.org/archives/intel-gfx/2010-February/005803.html]("http://lists.freedesktop.org/archives/intel-gfx/2010-February/005803.html")

But I don't understand what it is saying. The only problem with that whole bug page is that it is saying that the bug was only hendering X but I don't even have an X installed on this. Further more at the end of that thread it has an installable package but since I can't boot I can't do that. The only thing I'm thinking will fix it is the above patch BUT I'M CONFUSED! Reading the patch it looks like its something that I can boot from a liveCD and alter a couple files but I can't really tell from it which ones or how. Can someone translate it to something in a little more plain english, or has anybody ran into this problem before? Will a reinstall completely fix it or will it happen again? ANY help is greatly appreciated.

---

### Post by onyxwolf on 2010-04-19
Ok maybe 9.10 isn't the best to stick on something to "just work" and reliably. I don't mind having to occasionally tweak my laptop, but servers, no. So I went ahead and reinstalled with Hardy. Considering its LTS and has a couple years under its belt. Maybe in a couple years (when it gets close to the 2013 cutoff of Hardy's support) I'll up to 10.04 since it'll have a couple years of working out bugs by then!

In no way do I mean to put down Ubuntu. There is no other OS I'd run, or trust to be as stable. I'm just saying that the latest and greatest isn't exactly the best solution for a reliable DNS/openvpn server where stability may be a little more important.

---

