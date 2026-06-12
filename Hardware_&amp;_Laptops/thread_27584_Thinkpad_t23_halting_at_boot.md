---
title: "Thinkpad t23 halting at boot"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by synic on 2005-04-16
Hey folks.

Just installed Hoary on a Thinkpad t23.  It halts after "Uncompressing kernel... OK, loading linux..."

I've found that if I pass "acpi=off" to the kernel, it boots ok.  I'm just wondering what part of ACPI might be causing the problem?  Obviously I want some ACPI.... it being a laptop and all.  I've had ACPI working perfectly with some other distros, so I know at least parts of it work.

Any ideas would be appreciated.

Adam

---

### Post by Toddy on 2005-04-16
Hi Adam.  I had the same issue on a previous T23 ThinkPad.  After you boot up using the "acpi=off", go to Synaptic and install the "linux-686" package.  You should boot fine with the 686 kernel.

---

### Post by synic on 2005-04-17
Thanks - that did the trick.

One other thing, my sound doesn't seem to be working.  The modules appear to be loaded, but I get absolutely no sound.  Any ideas?

---

