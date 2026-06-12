---
title: "Legion Y740 WiFi won't work with Lunar Lobster 23.04"
date: 2023-05-03
forum: Hardware
---

### Post by moatl1977 on 2023-05-03
I'm running my Lenovo Legion Y740 laptop on Ubuntu since 2020-07; WiFi worked well until I updated to Lunar V23.04 last week. Since then the WiFi isn't recognized any more at all. 
The Network controller is recognized as:  Network controller: Intel Corporation Cannon Lake PCH CNVi WiFi (rev 10)
HW-module iwlwifi-compat does not work and trying to load module iwlwifi comes up with an error: "Invalid argument". 
I tried installing and removing the different iwlwifi kernel-packages; unfortunately without success.

---

### Post by noasakurajin on 2023-05-07
I has the same porblem different laptop and wifi card but also the iwlwifi module that broke.
What fixed it for me was uninstalling the precompiled modules and then installing the 'backport-iwlwifi-dkms' package.
After that I only had to run 'sudo modprobe iwlwifi' and the wifi worked.

---

### Post by moatl1977 on 2023-05-09
Thank you – that solved the problem for me as well – even after a reboot (and that is what counts).  :D
I think I did this before (some how), but loading the module got me an error message before every time… 

Can I set this thread to solved by myself – I ask for a friend? ;)

---

