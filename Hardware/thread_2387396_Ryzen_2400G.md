---
title: "Ryzen 2400G"
date: 2018-03-18
forum: Hardware
---

### Post by gwilly7 on 2018-03-18
Just installed 18.04 beta with no problems however my mb is an Asus b350m-e and hdmi is only rated at 1.4. In Windows I have no problem getting 4k@60hz and from reading this is because Windows lets the processor determine the hdmi port speed but linux gets this info from a bios table if I understand correctly. Is there anyway around this with ubuntu or do I have to wait for new motherboards with actual hdmi 2.0 certification.

---

### Post by gwilly7 on 2018-03-19
I found this patch, is this something I can apply in ubuntu 

[https://bugs.freedesktop.org/show_bug.cgi?id=102820](https://bugs.freedesktop.org/show_bug.cgi?id=102820)

---

### Post by Yellow Pasque on 2018-03-20
The patch was commited in kernel 4.16-rc5: [https://github.com/torvalds/linux/commit/caf0a9030d75509f3cacefe466d6d69d26e3dee6#diff-ea948dc0e5703553cbab42523a57aba7](https://github.com/torvalds/linux/commit/caf0a9030d75509f3cacefe466d6d69d26e3dee6#diff-ea948dc0e5703553cbab42523a57aba7)

So you can try a "mainline" kernel:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16-rc6/)

---

### Post by gwilly7 on 2018-03-20
> **Temüjin said:**
> The patch was commited in kernel 4.16-rc5: [https://github.com/torvalds/linux/commit/caf0a9030d75509f3cacefe466d6d69d26e3dee6#diff-ea948dc0e5703553cbab42523a57aba7](https://github.com/torvalds/linux/commit/caf0a9030d75509f3cacefe466d6d69d26e3dee6#diff-ea948dc0e5703553cbab42523a57aba7)

So you can try a "mainline" kernel:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16-rc6/)


Thank you,

Very odd but I was able to get 4k@60 when going directly through my receiver instead of going straight to my tv.  Now I just need to figure out hdmi audio passthrough.  I am able to get 5.1 sound but no passthrough.

---

### Post by experimancer on 2018-05-27
The best and optimal way to run any Linux distro in AMD Ryzen5 2400G is to use kernel 4.17 or later and upgrade the graphics modules to MESA 18.2. Any other 'solution' will not get you there &#55357;&#56899;

Michael Laravel in Phoronix had done some quite extensive tests on Raven Ridge APUs on Linux: [https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1)

---

### Post by experimancer on 2018-05-27
More info here: [https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1)

---

