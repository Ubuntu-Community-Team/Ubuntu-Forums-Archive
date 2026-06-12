---
title: "Is there a fix for laptop sandy bridge overheating issue?"
date: 2012-06-23
forum: Hardware
---

### Post by vadboy on 2012-06-23
My laptop is:
Sony Vaio SB
Intel Core i7 - Sandy Bridge
4 GB of RAM
HDD drive
hybrid video card - 3000 intel and AMD 6470M

I have installed Ubuntu 12.04 on the day of its release, however I couldn't use it then since my laptop would overheat to the point ubuntu would freeze completely. I managed to restart my computer by going outside, to -7 degrees celcius and cool it down. 

Is there a fix to the overheating problem? I heard that its a common problem for sandy bridge laptops, and that kernel 3.4 should fix it.

---

### Post by shwallace on 2012-06-24
This isn't a fix but I have an HP laptop that overheats and I've found if I put it in suspend mode for a few minutes, it seems to work fine for a hour or two before I need to do it again.

---

### Post by ilpup on 2012-08-22
of course there is. I have a Sony SE (sandy bridge, ati hd6630m) series and I manage to install Ubuntu 10.04 (I think latest version 12.04 should work also) without problems. In 10.04 you have to install kernel 3.2.xx and additional Glasen repos in order to use Intel hd3000
Also, you have to shut down the ATI card using acpi_call module:
[http://cisight.com/switch-off-ati-vga-in-dual-vga-with-intel-on-ubuntu-to-solve-overheat-problem/](http://cisight.com/switch-off-ati-vga-in-dual-vga-with-intel-on-ubuntu-to-solve-overheat-problem/)

Finally, kernel boot options  **pcie_aspm=force**, **i915.i915_enable_rc6=1**, **i915.i915_enable_fbc=1** and **i915.lvds_downclock=1** must be added to GRUB.
After that,  my idle temperature is 37 °C, noise and temperature like in windows

---

