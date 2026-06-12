---
title: "Nvidia driver non-existant for Dell Latitude E5440 on Ubuntu 21.04"
date: 2021-09-30
forum: Hardware
---

### Post by espressobeanie on 2021-09-30
Hi!

My laptop is a Dell Latitude E5440
My OS is Ubuntu 21.04 x86_64
My Nvidia card is: VIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M]

When I go to type: ```
ubuntu-drivers devices
```

Nothing happens. No output.

I'm running the noveau drivers however I should be able to support the driver up to 390.144. Any idea how I would install it and switch to using that driver as the primary?

---

### Post by QIII on 2021-09-30
Hello!

Is this a hybrid graphics arrangement with both Intel and Nvidia graphics?

Have you used the EFI/BIOS to set the Nvidia GPU as the preferred?

---

