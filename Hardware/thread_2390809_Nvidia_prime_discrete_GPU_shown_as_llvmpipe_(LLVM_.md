---
title: "Nvidia prime discrete GPU shown as llvmpipe (LLVM 6.0)"
date: 2018-05-02
forum: Hardware
---

### Post by freckts on 2018-05-02
My girlfriend just bought a Dell laptop with Ubuntu and updated to 18.04. But I saw that in Preferences > About shows the "graphics" as llvmpipe (LLVM 6.0, 256bits). "lspci -k" command shows that Nvidia MX150 is using "nouveau" driver and Intel UHD 620 "i915". Ubuntu additional drivers shows that Nvidia-prime (opensource) is being used. I uninstalled nouveau (it still was showing in the additional drivers but Nvidia-Prime disappeared, so I selected Nvidia 390 and when I reboot it was using Nvidia drivers and showing the correct card name (and the Nvidia driver in "lspci -k", but when I select Intel in Nvidia-settings, after a long time and the app freezing, it tells me to reboot my computer and when I do it, changes back to llvmpipe and nouveau driver in lspci (I even uninstalled the f***ing driver).
The battery is dying with 2:30h (medium brightness and LTP configured) and it was supposed to last 4~5h, maybe it is related to screwed up drivers?
Thanks in advance, and sorry if I'm not being clear, English is not my native language

---

### Post by howler4x4 on 2018-05-10
Try again, my machine saw new O/S update just today. Also check for newer NVIDIA driver, one was available for my card. 
p.s. Your English is very good.

---

