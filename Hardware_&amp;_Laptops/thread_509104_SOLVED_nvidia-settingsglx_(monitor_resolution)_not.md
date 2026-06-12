---
title: "SOLVED: nvidia-settings/glx (monitor resolution) not persistent between X sessions"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by sonicdevo on 2007-07-25
I'm running Ubuntu 7.04, used "Restricted Drivers Manager" to install the nvidia-glx package, used nvidia-setting program to configure my monitor and card just fine.  However, the (correct) higher resolution for my monitor would always revert to the 1024x786 (incorrect) resolution between X sessions.  Turns out, the nvidia-settings program wasn't writing to xorg.conf correctly.  I had to copy the generated xorg.conf file from the "Preview" function of the nvidia-settings program and pasted it into xorg.conf (replaced the entire file), then saved and restarted X.  It's kept my settings ever since.

Obviously, it wouldn't hurt to backup your original xorg.conf

Vid Card: GeForce 7600

---

### Post by Cavalier1723 on 2007-07-25
I believe a simpler solution to be to run nvidia-settings using gksudo.

-

---

