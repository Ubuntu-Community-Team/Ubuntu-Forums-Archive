---
title: "JUST UPDATED now NVIDIA KERNEL MODULE issue."
date: 2005-11-30
forum: Hardware &amp; Laptops
---

### Post by persis on 2005-11-30
Hi.  Just peformed a regular update using synaptic and restarted the computer.  My display is an Apple Cinema 20" and using a NVIDIA GEFORCE FX5200

It has worked fine for months.  Now when I boot up X doesn't load and I get the error 

"Failed to load the NVIDIA kernel module"
 --- Aborting ---
"Screen found but not have usable configuation"

Anyone have an idea as to how the update modified the system - created this problem?

Thanks

---

### Post by nocturn on 2005-11-30
[QUOTE=persis]Hi.  Just peformed a regular update using synaptic and restarted the computer.  My display is an Apple Cinema 20" and using a NVIDIA GEFORCE FX5200

It has worked fine for months.  Now when I boot up X doesn't load and I get the error 

"Failed to load the NVIDIA kernel module"
 --- Aborting ---
"Screen found but not have usable configuation"

Anyone have an idea as to how the update modified the system - created this problem?

Thanks[/QUOTE]

The Nvidia module is in the restricted-modules packages, reinstalling it may help.

If it doesn't, as a workarround, you can switch to the NV driver, just replace nvidia in your xorg.conf file with nv and it should work.  That way you have X till this is solved.

---

### Post by persis on 2005-11-30
Indeed - switching from "nvidia" to "nv" does work,
however - I would like it to do as before - using the nvidia module in the restricted modules package.  But I'm unable to find the nvidia kernel module in the restricted package... hmmm - darn - any advice

[QUOTE=nocturn]The Nvidia module is in the restricted-modules packages, reinstalling it may help.

If it doesn't, as a workarround, you can switch to the NV driver, just replace nvidia in your xorg.conf file with nv and it should work.  That way you have X till this is solved.[/QUOTE]

---

### Post by nocturn on 2005-11-30
[QUOTE=persis]Indeed - switching from "nvidia" to "nv" does work,
however - I would like it to do as before - using the nvidia module in the restricted modules package.  But I'm unable to find the nvidia kernel module in the restricted package... hmmm - darn - any advice[/QUOTE]

Can you check this package: nvidia-kernel-common?

What happens if you open a terminal and issue the command:
sudo modprobe nvidia

---

### Post by tonderai on 2005-11-30
I just had a similar problem, and solved it by:

> sudo apt-get install linux-restricted-modules-2.6.12-10-686

The nvidia module now loads fine. The problem may be caused by changing from the 386 to 686 kernel? I had just done this, and Persis had run synaptic.

---

