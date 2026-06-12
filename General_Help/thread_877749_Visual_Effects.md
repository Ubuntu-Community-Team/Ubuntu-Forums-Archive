---
title: "Visual Effects"
date: 2008-08-02
forum: General Help
---

### Post by Paul Earland on 2008-08-02
When I try changing my Visual Effects from None to Normal I get message "Desktop effects could not be enabled".
Paul

---

### Post by StOoZ on 2008-08-02
do you use Nvidia gfx card?
if so go to : System ->Admin -> hardware drivers.

and enable it.

---

### Post by fragos on 2008-08-02
Visual effects require that you have a graphic that support 3D direct rendering. Open up a terminal window and run "glxinfo |grep render" and that will tell you if direct rendering is enabled. Running "lspci |grep VGA" will tell us what video card you have.

---

### Post by weweboom on 2008-08-02
did you download the compiz affects manager?

---

### Post by Paul Earland on 2008-08-02
> **fragos said:**
> Visual effects require that you have a graphic that support 3D direct rendering. Open up a terminal window and run "glxinfo |grep render" and that will tell you if direct rendering is enabled. Running "lspci |grep VGA" will tell us what video card you have.

Video card comes up as:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
Paul

---

### Post by fragos on 2008-08-02
The TNT2 is an older model card not supported by newer divers. "nvidia-glx-legacy" is the correct driver package for that card. Synaptics can tell you which if any of the 3 "nvidia-glx" packages are installed.

---

