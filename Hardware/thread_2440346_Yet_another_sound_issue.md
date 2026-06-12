---
title: "Yet another sound issue"
date: 2020-04-09
forum: Hardware
---

### Post by harry5552 on 2020-04-09
Hi, installed Ubuntu 19.10 on my Asus Zenbook Flip 15 alonside pre-installed Windows 10.

Loads of problems I guess because its pretty new hardare but the biggest one I cannot sort out is there's no sound from the internal speakers.

The audio drivers appear to be working as per sound level in attachment below and I think proven by attaching a bluetooth speaker works fines - looks to me like it's the Speakers!
[ATTACH=CONFIG]285467[/ATTACH]

















Tried pretty much everything I can find on this "common" issue on the web but still no joy, the sound is by harman/kardon if that helps and sudo lspci -v shows -

00:1f.3 Audio device: Intel Corporation Device 02c8 (prog-if 80)  
    Subsystem: ASUSTeK Computer Inc. Device 194e
    Flags: bus master, fast devsel, latency 32, IRQ 152
    Memory at c4318000 (64-bit, non-prefetchable) [size=16K]
    Memory at c4100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] Vendor Specific Information: Len=14 <?>
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, sof_pci_dev

any ideas (litterally any), guys? this is doing my Nut in. It's a lovely piece of kit and really don't want to return it

thanks

---

### Post by Yellow Pasque on 2020-04-09
[https://bugzilla.kernel.org/show_bug.cgi?id=206589](https://bugzilla.kernel.org/show_bug.cgi?id=206589)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1861009](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1861009)

---

### Post by harry5552 on 2020-04-09
> **Yellow Pasque said:**
> [https://bugzilla.kernel.org/show_bug.cgi?id=206589](https://bugzilla.kernel.org/show_bug.cgi?id=206589)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1861009](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1861009)

thanks for that, will take a look in a bit but wasted so much time getting no where with this, had to bite the vile-tasting bullet in the meantime and (Gulp!), get Win 10 configuration up to spec! I detest MS as much as the next but at least I can get some work done

---

### Post by Yellow Pasque on 2020-04-09
Unfortunately, there's not much to look at. Basically, I'm pointing out that others have the same problem and you can follow along with the bug reports. Other Zenbooks using the Realtek ALC294 codec have needed quirks to get the speaker working (Example: [https://github.com/torvalds/linux/commit/0bea4cc8383519f78f3f74caca7bdebdfb346d3b](https://github.com/torvalds/linux/commit/0bea4cc8383519f78f3f74caca7bdebdfb346d3b) )
Hopefully, it is something simple like that.

---

### Post by harry5552 on 2020-04-10
will keep an eye on it then and report back if I make any progress - thanks once again

---

### Post by harry5552 on 2020-05-25
> **harry5552 said:**
> will keep an eye on it then and report back if I make any progress - thanks once again

wahoo at last found this which fixed it, [https://bugzilla.kernel.org/show_bug.cgi?id=206589](https://bugzilla.kernel.org/show_bug.cgi?id=206589) - comment 2

I have sound :guitar:

---

