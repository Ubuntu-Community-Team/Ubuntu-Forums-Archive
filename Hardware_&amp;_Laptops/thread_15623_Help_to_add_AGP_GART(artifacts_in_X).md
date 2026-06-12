---
title: "Help to add AGP GART(artifacts in X)"
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by songochain on 2005-02-15
Hi guys i've asus a4k laptop with nforce3 mobo (amd64 3200+ mobility,ati mobility 9700)
I found the problem with artifacts with xorg, xfree also with all distributions i've installed. I need to add apg gart to kernel or add some module to fix artifacts. I added this line to xorg.conf but it isnt the solution
```
Section Device
...
Option "UseInternalAGPGART" "yes"

```I looking for a patch or something but i dont find nothing yet. Anyone knows what i have to fix it??
Thanks

---

### Post by Strider on 2005-02-15
I know there's an option for this in the kernel.  You'll need to check the config file to verify if this option is on or not.  I think by default it is.  If you look under /boot there should be a "config*" file.  Search for CONFIG_AGP and see if it's set to "m" or "y".  On my system the kernel I installed from the repository did have that option enabled.

Have you tried setting "UseInternalAGPGART" to "no"?  I have mine set to no.  Probably not much help.

---

### Post by songochain on 2005-02-15
Thanks 4 reply, config_agp is Y also gart but in windows if i dont install nforce drivers i get artifacts like in linux so i think that i must to install a patch. I view in some webs that there is a nforce2 patch but it's 4 32bits version and i dont see nothing about nforce3 :(

---

