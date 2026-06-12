---
title: "Nvidia 550ti not recognized using any Nvidia meta-packages"
date: 2020-05-27
forum: Hardware
---

### Post by hectorc2 on 2020-05-27
Ubuntu 20.04
Nvidia GTX 550ti
Intel i3-2100
Asus P8Z68-V LX motherboard

I am having an issue with all of the available meta-packages located in "Additional Drivers."
My monitor is not being detected, I am forced to 800x600 resolution, and when I open "NVIDIA X Server Settings" the window is blank.
I have tried meta-packages:440(the recommended driver) , 435, and 390 rebooting after each install with exactly same result.
The binary driver version 340.108 works fine.
The Nouveau driver work fine as well.
I appreciate any help you can provide.

---

### Post by CatKiller on 2020-05-27
390 is the last branch that supports that card. That branch won't keep working with new kernels indefinitely, since it's no longer maintained.

You need to purge an existing branch before installing a new branch, otherwise it fails.

---

### Post by hectorc2 on 2020-05-27
Thank you for the quick response.
I do wish that the installer wouldn't default to an incompatible driver when the proprietary drivers are selected, but oh well.
I suppose I will try to google how to purge the drivers or if I'm feeling lazy I may just reinstall the OS, I kinda wanted to try Kubuntu again.
Its crazy these days that it's so easy to install an OS(if you backup you data).
Thanks again.

---

