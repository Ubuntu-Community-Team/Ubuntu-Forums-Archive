---
title: "Ok hardware?"
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by OldPlanet on 2005-11-24
I am going to buy a new computer, and i am wondering if Ubuntu will work flawless with a Gigabyte GA-K8NF-9 motherboard and a Hightech Excalibur Radeon X300SE 128MB graphics-card. I have heard some people are having trouble with PCI express cards? I do not want to use ATI's proprietary driver, so, is it supported by X.Org's radeon-driver?

---

### Post by frodon on 2005-11-25
If you want linux to be your first OS i strongly advice to buy a nvidia card because you will get a better support.

---

### Post by OldPlanet on 2005-11-25
All my my current computers are running [Arch Linux]("http://www.archlinux.org/") or [FreeBSD]("http://www.freebsd.org/") exclusively, all with ATI-cards.

I don't want to use any proprietary driver, that is not an option. As far as i know, X.Org's nv-driver is terrible, while the radeon-driver is just fine (but no 3D-acceleration). This new computer is for my parents. I don't need any 3D-acceleration, and neither do they. So if the X300SE card works well with X.Org's radeon-driver, everything is fine.

---

### Post by frodon on 2005-11-25
i think it should.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?)

---

### Post by OldPlanet on 2005-11-25
Thanks, my parents new computer will be running Ubuntu exclusively then. :smile:

---

### Post by metoo on 2005-11-25
Good luck!

ATI Graphics and NForce chip set?

You pair the worst of both worlds. :-)

It's been a while, but I once had a nforce chip set and an ATI graphic cards. Never again. As good as nvidia graphics supports Linux, so bad does the nforce chip set division.
Why is the forcedeth, a re-engineered nforce network driver in the kernel?? Audio can be a problem on the nforce4 (might only be the digital out part).
In the windows world nforce4 is better (faster) than the rest, in Linux I would avoid it.
Go VIA with the chip set (not the very new southbridge! ..51? or ..57?)
The ubuntu kernel is pretty old. Updates not in sight.

And why mess with ATI if you can have NVidia?

Even when only surfing, 3D will make the system a tick snappier. Setting up 3D nvidia is fairly easy, as the drivers are already in the linux-modules-restricted-yourkernel package.

---

