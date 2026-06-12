---
title: "Is my GPU dead? Several problems occurred suddenly (+ cannot boot properly)"
date: 2011-03-05
forum: Hardware
---

### Post by hurpdurp on 2011-03-05
Hi,

I am horribly afraid my GPU is dead – it all started a few days ago, when all of a sudden while I was browsing, the hues shifted to pink (where it previously appeared as a dark color) and a shutdown occurred without me interrupting or interacting. Afterwards I could boot with no problems, as if nothing had happened. Everything was normal, screen resolution was normal, hues were normal, etc.

However, unfortunately the same thing happened again randomly. After the hues changed rapidly from one color to another, my machine shut down, and all hell broke loose. When attempting to boot, I could not recognize any problems until the boot stage almost had completed – the BIOS, GRUB and the Ubuntu loading bar worked properly, however here the idyll completely stopped. After the loading bar had vanished, but before having the opportunity to log in, everything froze and the CPU went wild – I could very well hear the fans spinning faster than ever before.

And then, I simply had to reboot again to no avail. The same thing happened, over and over, again. I was doomed. The GPU – is it really dead?

As a final resort I booted into low graphics mode (800x600). Which works, and I’m still confined within this pernicious screen resolution (my eyes!). Obviously I’m not using my GPU anymore (correct me if I’m wrong) so this might prove my assumptions completely true.

While actually having access to my beloved Ubuntu, I have tried to change my nVidia driver numerous times, yet again to no avail. I’m really out of ideas now. What can I do? Is there any hope for me, or should I simply get rid of this laptop and buy another one? I should mention it’s 4 years old now.

Anyway, if this is of any help, take a look:

```

uname -r
2.6.35-27-generic

```

```

lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8600M GS] (rev a1)

```

I’ll obviously and happily provide any other relevant information needed. I’d be grateful for any answers. Thanks in advance!

**tl;dr:** I think my GPU is dead, I cannot properly boot, low graphics mode only works, I’m stuck in 800x600, I have tried numerous different ways to solve this problem, changed drivers, etc. What should I do?

---

