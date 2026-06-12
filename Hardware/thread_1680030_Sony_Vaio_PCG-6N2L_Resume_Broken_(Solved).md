---
title: "Sony Vaio PCG-6N2L: Resume Broken (Solved)"
date: 2011-02-01
forum: Hardware
---

### Post by Professor Gordini on 2011-02-01
Folks, I inherited a Sony Vaio PCG-6N2L and installed Ubuntu 10.04 on it. The computer suspends fine when I close the lid, but when I try to resume, it shows me a mangled gray moire-type pattern (not the plain-vanilla X screen, but a bit similar).

Anyway, I Googled around and got a bit of a lead which helped me to solve my issue and I just wanted to share it here in case anybody else has this issue.

Go to System->Administration->Hardware Drivers and pick the "NVIDIA accelerated graphics driver (current version) [Recommended]" option. Ubuntu then downloads some drivers and such. It took a while (maybe 5 minutes) on my machine, then it recommended that I reboot. After rebooting, the suspend/resume cycle works properly.

See the attached "Screenshot-Hardware Drivers.png" screenshot for a view of the Hardware Drivers configuration screen after installing the NVIDIA driver.

P.S. Ubuntu guys: you're doing great work. I've been using Linux since the old days when Yggdrasil and Slackware were popular, but Ubuntu was the first Linux distro where I could plug in a digital camera/USB mass storage device/etc. and have it work without a crapload of headaches :) Thanks for all your hard work.

---

