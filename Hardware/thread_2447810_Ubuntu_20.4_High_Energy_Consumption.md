---
title: "Ubuntu 20.4 High Energy Consumption"
date: 2020-07-26
forum: Hardware
---

### Post by sebastian23 on 2020-07-26
Hi! I bought a new Acer Laptop (ConceptD 5 CN517-71-74YA) which is quite powerful, but also consume a lot of energy.
When I use this Laptop with Windows the battery lasts almost three hours, but when I use Ubuntu, just for browsing the web or office use, the battery just lasts half of this time. Is there any energy saving option I could activate under Ubuntu 20.4?

---

### Post by ajgreeny on 2020-07-26
Install tlp.
It will configure itself to run automatically at boot with settings which are probably fine for the machine though you can edit them if needed; I've  never needed to on my laptop

---

### Post by Yellow Pasque on 2020-07-27
Are you running on the Intel or Nvidia GPU? Windows does Optimus switching seamlessly and transparently. On Linux, it takes more wrangling to get the GPU situation right on such setups.

---

### Post by CelticWarrior on 2020-07-29
> **Yellow Pasque said:**
> Are you running on the Intel or Nvidia GPU? Windows does Optimus switching seamlessly and transparently. On Linux, it takes more wrangling to get the GPU situation right on such setups.

This means that Windows is using the energy saving iGPU by default, only switching to the more energy demanding dGPU when needed. This switch is done automatically. Not so in Linux (yet).

Very likely you're using the dGPU by default in Ubuntu and that alone accounts for the difference. Please open Nvidia X Server settings and then Profiles to check. For your reported usage - *just for browsing the web or office use* - and media there's absolutely no point in using the dGPU, the iGPU is more than enough for all of that and more.

---

### Post by sebastian23 on 2020-07-30
> **CelticWarrior said:**
> Very likely you're using the dGPU by default in Ubuntu and that alone accounts for the difference. Please open Nvidia X Server settings and then Profiles to check. For your reported usage - *just for browsing the web or office use* - and media there's absolutely no point in using the dGPU, the iGPU is more than enough for all of that and more.

Thank you CelticWarrior, you was absolutly right, NVIDIA Performance Mode was selected there. I switched it to Intel Power Saving Mode and Battery lasts much longer now. If I select NVIDIA On-Demand Ubuntu will switch between Intel and NVIDIA automatically if necessary, or better just leave the option on Intel?

I also installed tlp as  		ajgreeny said, but couldn't see any difference through that.

---

