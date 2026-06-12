---
title: "Can't set brightness"
date: 2010-07-06
forum: Hardware
---

### Post by LucasLinard on 2010-07-06
Hi,
I have a samsung R430 notebook. The some Fn keys are not working (only vol +- work) I cant set the brightness or turn o the wireless network.
Can anyone help. I've tried adding GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux" to /etc/default/grub as sugested on another post. It didn't work.

---

### Post by scott1541 on 2010-07-06
To set the brightness you can go into the system menu, then preferences and then find power management. In there you can set the brightness.

---

### Post by LucasLinard on 2010-07-06
It is not working. I set the brightness but the screen remains the same.

---

### Post by scott1541 on 2010-07-06
> **LucasLinard said:**
> It is not working. I set the brightness but the screen remains the same.

Did you set the brightness for both on battery and mains. 

^That is the extent of my knowledge.

---

### Post by cronot on 2010-08-20
I've a Samsung R430 too. This line "sort of worked" for me on /etc/default/grub :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"

It "sort of worked" because the FN + Up / Down (to increase / decrease brightness) still doesn't work. But at least you can now adjust the brightness on the Power settings, and the display correctly dims when the system is idle or when you're running on the battery. For some reason, adjusting the brightness with the brightness applet doesn't work though. Also, the above options makes you lose the boot splash screen, but that's no big deal for me.

I got this line from this: [https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948)

This whole brightness setting problem (at least the part about setting it within Ubuntu) seems to be a problem on the Intel Graphics 4 driver for Linux, which seems unresolved so far, and affects many other laptop models from other brands. As for the FN+UP/DOWN keys issue, I don't think that will be solved in the near future because it seems Samsung has gone with a very customized implementation for this; e.g.: I can't use the FN+UP/DOWN and FN+F9 for brightness setting and toggling wireless on Windows 7 either unless I install a couple of applications from Samsung, IIRC: "Easy Display Manager" and "Easy Network Manager", which you can find here: [http://www.samsung.com/us/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=05012600&prd_mdl_cd=NP-R430-JA01US&prd_mdl_name=NP-R430I&prd_ia_sub_class_cd=P](http://www.samsung.com/us/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=05012600&prd_mdl_cd=NP-R430-JA01US&prd_mdl_name=NP-R430I&prd_ia_sub_class_cd=P)


Cheers!

---

### Post by jfr_br on 2010-11-25
I have same problem. Someone find the solution?

---

### Post by governmentproj13 on 2010-11-25
I thought brightness was managed by power management?  What in ubuntu manages power?

---

### Post by governmentproj13 on 2010-11-25
So, I thought the acpi_backlight line fix didn't work for my computer, regardless of the variation, until I removed "nomodeset". For some reason, typing that screws up things for me.  I have a really nice nvidia card and drives on my laptop, and I never had a problem with them with my model, so I probably don't need to disable nouveau.  Anyway, for those still having trouble, I thought listing this might potentially help some.

---

