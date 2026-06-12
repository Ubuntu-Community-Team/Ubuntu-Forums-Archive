---
title: "Restricted Drivers Manager Problem"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by Apurva Misra on 2008-03-04
Hi all!
I have installed the latest NVIDIA driver for my integrated Geforce go 7150 (NVIDIA-Linux-x86_64-169.12-pkg2) from NVIDIA website. I installed it manually. Now the problem is that despite everything working fine, the restricted drivers manager shows that the driver for NVIDIA is "not enabled" (but the "in use" button is green). when i try to enable it, it replaces the driver with something similar to "nvidia_glx_new" and the glx support is gone (while trying to launch torcs, i get the error "no glx extension found for display :0.0") while the game runs perfectly with the former driver. 

the same happens when i try to select "Extra" visual efects in Appearance Preferences.... It asks me to enable the driver in the manager and on selecting "enabled" checkbox, the driver is replaced. I know that the downloaded driver is the correct one from NVIDIA support. What should I do?

please help!:confused:


--------------------------------------------
Compaq Presario V6608AU
1GB RAM, Intel Turion 64x2 processor
NVIDIA integrated Geforce Go 7150 graphics card
--------------------------------------------

---

### Post by Arand on 2008-03-04
For me, when installing the newest ATI drivers from ATI's homepage, the enabled box in restricted-drivers-manager should NOT be ticked, if you want to use the newest driver.

I presume that this is also how the NVIDIA drivers works to.

- Arand

---

### Post by Apurva Misra on 2008-03-04
> **Arand said:**
> For me, when installing the newest ATI drivers from ATI's homepage, the enabled box in restricted-drivers-manager should NOT be ticked, if you want to use the newest driver.

I presume that this is also how the NVIDIA drivers works to.

- Arand

thanx for the quick reply Arand. so, should i reinstall my driver with the box unchecked and then check it?

---

### Post by Arand on 2008-03-04
What I think you should do (observe that I know only about the ATI so I may be wrong) is:

- Disable the drivers from the restricted-drivers-manager, if you have enabled them there.

- Then install the NVIDIA drivers from their homepage.

- Then you shouldn't have to do anything with the restricted-drivers-manager, just leave it with the box unticked, since the only thing ticking this box does is to install the old NVIDIA drivers.

This is what the CCHTML unofficial ATI guide says about it:

> Please note that after the modification above, the "Restricted Driver Manager" will signal "ATI accelerated graphics driver" not enabled (unticked). This is perfectly correct. At the end of the installation procedure it will signal in Status: "in use" (green light), but NOT enabled. It simply means that the fglrx module contained in the linux-restricted-modules package is not enabled, but another fglrx module (7.12) is in use. 


- You might have to reinstall Compiz Fusion to get it working with the new driver. You can do that as described under the "Install Compiz Fusion" section here: [https://help.ubuntu.com/community/CompositeManager/CompizFusionATI#head-958a1bad18942c1f683aba018f2d970c3f91d188](https://help.ubuntu.com/community/CompositeManager/CompizFusionATI#head-958a1bad18942c1f683aba018f2d970c3f91d188)

Again, I only know about the ATI drivers, but I am guessing that some things apply to NVIDIA as well.

- Arand

---

