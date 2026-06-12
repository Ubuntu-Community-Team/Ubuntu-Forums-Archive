---
title: "Brightness Adjust Does Not Work"
date: 2012-04-02
forum: Hardware
---

### Post by cbennett926 on 2012-04-02
As the title says, I have a Lenovo w520 and the brightness keys display a change in the brightness, however it does not change. I am running discrete graphics, as well as the most up-to-date Nvidia driver from their website. I set the settings to not dim in the mean time and so far it is working, but once it dims, it will not come back from dim. The screen will also not darken if I attempt to change it with keys, or through system settings.

---

### Post by wojox on 2012-04-02
Check out this bug report cbennet [[Lenovo W520] laptop freezes on ACPI-related actions ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/776999")

Look down a post #60. It looks like if you add a kernel option 'nox2apic' to the boot options and the nvidia-specific EnableBrightnessControl=1 option in xorg.conf solved the problem.

---

### Post by cbennett926 on 2012-04-02
Once again you are here to save the day, by any chance can you help me do this though? I have no idea how to use xorg

---

### Post by cbennett926 on 2012-04-04
Ah! I got it all figured out, and the problem has been corrected!

---

