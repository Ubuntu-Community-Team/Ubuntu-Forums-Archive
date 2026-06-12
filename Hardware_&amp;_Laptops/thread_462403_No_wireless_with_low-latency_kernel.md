---
title: "No wireless with low-latency kernel"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by thevoice on 2007-06-02
I've recently installed the low latency kernel for use with the Ubuntu Studio packages and I now have no wireless connection when using it.  I have used lsmod to verify that the correct module is present (ipw3945), but I still get no wireless interface.

If I reboot with the generic kernel then everything is as normal, without making any other changes.

Any ideas?

---

### Post by rexey on 2007-06-02
Yea, I had this too
If you click on the link to Restricted Drivers Manager it tells you it's missing the Linux-restricted modules
So...
hook up with a wired connection,
search Synaptic for linux restricted modules and find the one that matches the version of the low latency kernel.

-Rexey

---

### Post by thevoice on 2007-06-03
Cheers, that worked.  Oddly I tried that yesterday and synaptic complained it couldn't find the package, don't know what was different today...

---

### Post by deadguy87 on 2007-06-07
Remember everytime you try a new kernel to remember to install the restrictive driver manager. I had the same problem a while back, but when Scrolling through the synaptic package manager I found the restrictive mananger and that fixed it, it also fixed it when I was working around the sound problem that I have when I first installed Fiesty Fawn

---

