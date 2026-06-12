---
title: "Kernle upgrades should mount boot"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by Ateo on 2009-01-28
I just don't get it. Ubuntu tries to automate everything to make things easy. Kudos for that.

However, I find one thing that just doesn't make sense. Why doesn't boot get mounted when installing an new kernel? This leads to disaster.

So, my question is... Why does apt-get not mount boot when needed?

---

### Post by kidders on 2009-01-29
Hi there,

I don't get this one either. It's as though anyone with a reason to deviate from a "default" single-filesystem install is expected to be able to anticipate problems their customisations might cause.

Automatically mounting /boot would surely be trivial ... and you can hardly be the first person in the world to learn the hard way that you need to do it manually. Perhaps you should check whether a bug has been filed about this.

---

