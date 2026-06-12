---
title: "Laptop with Intel 82801AA AC'97 Audio Controller - no sound or microphone :("
date: 2020-04-13
forum: Hardware
---

### Post by mrjohnc on 2020-04-13
Hi all

I have a Lenovo Yoga Chromebook C630 and have managed to install 19.04 successfully using chrx.org, the main issue I have (not fixed by updating to 20.04) is that sound and microphone don't work, sound is listed as 'Dummy Output' and there is simply no microphone listed. 'lspci' tells me it has a Intel 82801AA AC'97 Audio Controller, the only mention I can find of this device in Ubuntu is [https://manpages.ubuntu.com/manpages/xenial/man4/ichsmb.4freebsd.html](https://manpages.ubuntu.com/manpages/xenial/man4/ichsmb.4freebsd.html) 

How would I go about installing the correct drivers for it? 

Thanks very much

---

### Post by CelticWarrior on 2020-04-13
There's no reason to use an old and now unsupported release (19.04). Please install a supported release. A solution, if any, will come to the currently supported releases.

---

### Post by mrjohnc on 2020-04-13
I have 20.04 installed

---

### Post by Yellow Pasque on 2020-04-13
I would suggest trying a mainline 5.6.x kernel to see if this fixed it: [https://github.com/torvalds/linux/commit/5caf64c633a3564f70e734868254281b25932fc0#diff-e93fedb0e7cb7788666d764a8507bc41](https://github.com/torvalds/linux/commit/5caf64c633a3564f70e734868254281b25932fc0#diff-e93fedb0e7cb7788666d764a8507bc41)

---

### Post by mrjohnc on 2020-04-13
Thanks very much, this looks really promising, what specifically should I do to upgrade the kernel to this version? Will this version be used in 20.04?

---

### Post by Yellow Pasque on 2020-04-13
> Will this version be used in 20.04?

Not initially, but by the time 20.04.2 comes out, it should be available.

> what specifically should I do to upgrade the kernel to this version?

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.6.4/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.6.4/)

---

### Post by mrjohnc on 2020-04-23
Thanks very much, I've realised there is a problem with this approach. The fixes mentioned on github are for a different laptop (yes Lenovo decided to name two completely different laptops C630, one 15 inch Intel porcessor and one 13 inch ARM processor)...

Any other ideas?

---

### Post by ian-leedham on 2020-04-24
I'm am having a similar issue with a different laptop and the only temporary fix I have found is to do:
```
pulseaudio --kill; sleep 2s; sudo alsa force-reload ; pulseaudio --start
```

This fixes it until I restart

---

