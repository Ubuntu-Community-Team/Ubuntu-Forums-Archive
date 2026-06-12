---
title: "HDMI and Thunderbolt 3 not working when Intel is selected using prime-select"
date: 2020-05-13
forum: Hardware
---

### Post by gsync on 2020-05-13
Hello,

My machine is Legion Y740 with RTX 2070, with Ubuntu 18.04 up to date.

When the OS loads with only Intel selected as video driver,
using either Nvidia X Server Settings (GUI) or prime-select,
my HDMI and Thunderbolt 3 don't recognize external displays.

Is there a way I can select only Intel as video driver and still use my HDMI and Thunderbolt 3 ?

---

### Post by CelticWarrior on 2020-05-13
It's an hardware configuration, it doesn't depend on OS or drivers.

---

### Post by gsync on 2020-05-13
You mean - these ports are connected only to the RTX card, therefore cannot run without ?

---

### Post by CelticWarrior on 2020-05-13
> **gsync said:**
> You mean - these ports are connected only to the RTX card, therefore cannot run without ?

Exactly. It's the same is most (all??) notebooks with hybrid graphics.
The reason is if you're using an external monitor you have access to an electrical outlet therefore you can use the dGPU, leaving the iGPU only for traveling when battery life really matters.
Of course, it can be argued that users would benefit from using the iGPU as well with an external monitor to save energy but things are what they are.

---

