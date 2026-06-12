---
title: "Force removal of bad &quot;in-use&quot; drivers"
date: 2009-05-27
forum: Hardware
---

### Post by Something Else on 2009-05-27
So, I was trying to get my laptop's dial-up modem to work; long story short, I installed a device driver package from a .deb that I was told MIGHT work with my system, and might not. It didn't and the installation failed, but the package is now listed as a broken package in my apt tree, and nothing can be installed on my system until I can remove it. Unfortunately, it's installed several modules - hsfengine, hsfserial, and more - which my system claims are in use, even though the dial-up modem is not in use and I can't figure out any way to disable these components.

Regardless, I no longer care about the modem, but I need to remove these packages, since nothing can be installed until they are fixed.

---

