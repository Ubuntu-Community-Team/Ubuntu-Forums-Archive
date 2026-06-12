---
title: "i2c devices and vcc regulators."
date: 2024-04-30
forum: Hardware
---

### Post by alextwn on 2024-04-30
I've been using the same 20.04 image for quite a while, and it was OK to init i2c devices with dummy regulators.
E.g., pca953x 0-0025: 0-0025 supply vcc not found, using dummy regulator


About a month ago, an update happened (it wants to update fewer packages after the installation is complete), and now the same image on the same system gives me this:
pca953x 0-0025: incomplete constraints, dummy supplies not allowed
pca953x 0-0025: error -ENODEV: reg get err

Is there a way to disable this requirement?

---

