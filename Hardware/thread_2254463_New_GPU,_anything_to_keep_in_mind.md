---
title: "New GPU, anything to keep in mind?"
date: 2014-11-27
forum: Hardware
---

### Post by aquablue25 on 2014-11-27
Sup guys,

I just built a PC for a friend of mine and I already have Ubuntu 14.04.1 64-bit installed on it. The PC is using an Ati 3200 onboard IGPU, which is running with the default Open Source Radeon drivers provided by Ubuntu.

The plan now is to INSERT (/upgrade to) a Geforce GTS 450 GPU into the PC. Do I have to remove or configure anything before doing so or is it just plug and play (+ installing Nvidia drivers)?

Thanks,
Aqua

---

### Post by ajgreeny on 2014-11-27
After the change you may need to boot first time with the **nomodeset** option and then install whatever nvidia driver is available from Additional Drivers.  After that it should be fine.

Don't try to install the nvidia driver before the card is installed.

---

