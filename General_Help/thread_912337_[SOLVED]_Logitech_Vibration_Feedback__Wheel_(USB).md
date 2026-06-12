---
title: "[SOLVED] Logitech Vibration Feedback  Wheel (USB)"
date: 2008-09-06
forum: General Help
---

### Post by ^^rac on 2008-09-06
Hey guys!!

Is there anyway to make this work in Ubuntu?

---

### Post by ^^rac on 2008-09-20
Any news here?

---

### Post by holmes0 on 2008-09-23
Hi,

After hours of Google, I found only a few reports of successful use of Force-Feedback-enabled joysticks or wheels. It seems there are two conditions:
1) to have one of these devices:
* Logitech Cordless rumble pad */
* Logitech Cordless rumble pad 2 */
* Logitech Wingman Force 3d */
* Logitech Force 3D Pro Joystick */
* Logitech Formula Force EX */
* Logitech MOMO force wheel */
* Logitech MOMO force wheel */
* "Twin USB Joystick" */
* "GreenAsia Inc.    USB Joystick     " */
* FGT Rumble Force Wheel */
* FGT Force Feedback Wheel */
* MS Sidewinder Force Feedback 2 (experimental support)

2) to recompile the kernel with activation of the force feedback features.

I don't know if your particular wheel is one of these devices. Considering the kernel, some help is given in the Ubuntu community documentation. I tried the debian way (described in the documentation). You have to download the compilation tools, download the sources, modify the configuration (using xconfig or menufconfig). Then look for "Force Feedback" features and/or lines corresponding to you wheel in the Input part and ask the creation of module or direct integration into the kernel. Then you have to compile your new kernel and install it beside the current one. With GRUB, you can boot on your new kernel or the old one.
I personnaly went through this whole process last week. I could get effects into my SideWinder FF2 (and then a system freeze) with gforce-03. It is probably due to the experimental support of this particular joystick. Maybe it will work for you...
I think playing VDrift with a force-feeback wheel could be fun. I wish you good luck!

---

### Post by ^^rac on 2008-09-26
> **holmes0 said:**
> Hi,

After hours of Google, I found only a few reports of successful use of Force-Feedback-enabled joysticks or wheels. It seems there are two conditions:
1) to have one of these devices:
* Logitech Cordless rumble pad */
* Logitech Cordless rumble pad 2 */
* Logitech Wingman Force 3d */
* Logitech Force 3D Pro Joystick */
* Logitech Formula Force EX */
* Logitech MOMO force wheel */
* Logitech MOMO force wheel */
* "Twin USB Joystick" */
* "GreenAsia Inc.    USB Joystick     " */
* FGT Rumble Force Wheel */
* FGT Force Feedback Wheel */
* MS Sidewinder Force Feedback 2 (experimental support)

2) to recompile the kernel with activation of the force feedback features.

I don't know if your particular wheel is one of these devices. Considering the kernel, some help is given in the Ubuntu community documentation. I tried the debian way (described in the documentation). You have to download the compilation tools, download the sources, modify the configuration (using xconfig or menufconfig). Then look for "Force Feedback" features and/or lines corresponding to you wheel in the Input part and ask the creation of module or direct integration into the kernel. Then you have to compile your new kernel and install it beside the current one. With GRUB, you can boot on your new kernel or the old one.
I personnaly went through this whole process last week. I could get effects into my SideWinder FF2 (and then a system freeze) with gforce-03. It is probably due to the experimental support of this particular joystick. Maybe it will work for you...
I think playing VDrift with a force-feeback wheel could be fun. I wish you good luck!

Thanks alot for our effort!

---

