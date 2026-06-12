---
title: "Clevo P650RA laptop - i915 and NV GTX965M - How to help improve compatibility"
date: 2016-03-19
forum: Hardware
---

### Post by MadEgg on 2016-03-19
I recently bought a Clevo P650RA laptop. It has a Skylake Core i7 6700HQ processor and a NVidia GTX965M graphic chip. I'm having some issues that seem to be mostly related to video hardware.

The Clevo laptop has a setting in the BIOS that allows switching between MSHYBRID (Optimus) and DISCRETE (just the Nvidia chip).

To get the most recent driver support, I started out with Kubuntu Wily 15.10 setup but upgaded to Xenial after installation.

* During installation of the laptop, I had to switch to DISCRETE, because otherwise the boot process would get stuck. This uses the Nouveau driver during the installation, and puts me in a desktop running nouveau graphics. However, it's unstable: somwhere between 1 and 5 minutes, the system will come to a full freeze.
* I toggled to MSHYBRID, which dumps me in a desktop using the i915 driver. However, it seems to be using 16-bits color rather than 32-bits color, and the stability issue remains.
* I then installed the binary nvidia-361-updates driver. This gets me to a fully working desktop using nvidia graphics. Using nvidia-settings I can toggle between discrete graphics and IGP, however, when using IGP, I get a lot of visual corruption. So that means I'm forced to use the nvidia chip, even though this has significant impact on battery life.
* Ever since the binary drivers were installed, I am unable to switch back to DISCRETE in the BIOS again - if I do this it boots ok but is unable to start X.org. The Xorg.log does not show any error messages, and I can use the console fine, but there is no visual. Uninstalling the binary nvidia driver does not fix this: this makes Xorg completely unusable. It does not revert to nouveau-driver, even though I did remove the blacklist entry. This means that I'm now stuck at using the binary nvidia driver (of course, nouveau makes the system unstable, so that's not really attractive either).
* When the laptop is in DISCRETE using Nouveau drivers, the two buttons for adjusting the brightness of the screen work. However, when using MSDISCRETE or when using the nvidia binary drivers, they do not generate any event (not in XEV, not using evtest) (I found references pointing in the direction of ACPI implementation in i915 driver).

Most issues seem to point in the direction of the i915-driver (or actually, the i915_bpo driver with Ubuntu-provided backports).

I'm unsure on how to proceed. The laptop is currently usable with just the nvidia graphics using the binary driver, but I would like to contribute as much as I can in order to get better support for this hardware, so that I would be able to switch to the IGP when I don't have the need for discrete graphics in order to conserve energy.

Should I start posting bug reports to Ubuntu, or rather to kernel.org? Should I hijack similar threads / issues with different laptops using the same driver (even if they're 5 years old), or should I report new bugs? What info can I collect to best help identify the cause of the problems? Is there any additional software / alternative kernels / Xorg software that provide more helpful information? 

I'm already on the xorg-edgers repository, but since I'm running a not-yet-released version of Ubuntu, that's mostly in-sync with the Xenial repositories anyway.

Thanks for any pointers on how to contribute!

---

