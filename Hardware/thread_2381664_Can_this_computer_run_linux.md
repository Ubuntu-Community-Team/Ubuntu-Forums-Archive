---
title: "Can this computer run linux?"
date: 2018-01-03
forum: Hardware
---

### Post by br3adina7or on 2018-01-03
Hey! I'm not used to modern hardware, even less so in regards to linux, so could someone tell me if the computer linked below runs Ubuntu? (Or any linux distro, really)

[https://www.pcworld.co.uk/gbuk/computing/desktop-pcs/desktop-pcs/pc-specialist-vortex-minerva-le-pcs-d1180719-gaming-pc-10164366-pdt.html](https://www.pcworld.co.uk/gbuk/computing/desktop-pcs/desktop-pcs/pc-specialist-vortex-minerva-le-pcs-d1180719-gaming-pc-10164366-pdt.html)

---

### Post by QIII on 2018-01-03
Although I don't see any showstoppers, you'll want to disable the AMD graphics on the APU in your BIOS/UEFI so your graphics drivers don't collide.  Do that prior to attempting to install.

Still, it's hard to say up front with full certainty that an off-the-shelf machine will be free of issues.  I build my own machines after thorough research on the individual components.

Cheers!

---

### Post by ajgreeny on 2018-01-03
That company which I have used for two machines, both more basic Intel based, but both of which have worked faultlessly for 3 or more years with Ubuntu and Xubuntu, has a Linux forum which may help you if you search for that model.
[https://www.pcspecialist.co.uk/forums/forumdisplay.php?32-Linux](https://www.pcspecialist.co.uk/forums/forumdisplay.php?32-Linux)

---

### Post by gordintoronto on 2018-01-03
This post indicates it should work: [https://www.linuxquestions.org/questions/linux-newbie-8/asus-m5a97-r2-0-linux-compatible-4175613541/](https://www.linuxquestions.org/questions/linux-newbie-8/asus-m5a97-r2-0-linux-compatible-4175613541/)

It looks like the Wi-Fi is not on the motherboard, so it could be a problem.

---

### Post by Yellow Pasque on 2018-01-04
> **QIII said:**
> you'll want to disable the AMD graphics on the APU in your BIOS/UEFI so your graphics drivers don't collide.

The FX-4300 is not an APU. There are no integrated graphics on the system.

EDIT: Depending on which version of Ubuntu is used, you may need to boot with 'nomodeset' parameter for the installer and first boot. Then, you can install the nvidia driver.

---

### Post by QIII on 2018-01-04
Right you are, of course!  

Derp!  I need to read more carefully...  : )

---

