---
title: "issue installing ati driver in edgy"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by raim1312 on 2007-03-29
Ive used dapper for quite awhile and successfully installed the ati driver 8.26.18 for my radeon xpress 200m. i decided to see what other linux distros there where out there and found myself coming back to ubuntu and using the new edgy distro. trying to install the driver again i come across this error:

./ati-installer.sh: 163: Syntax error: Bad substitution

this is completely new to me and im unsure how to solve this issue. has anyone come across this problem before or they know how to fix it? thanks for your help

---

### Post by nachotronics on 2007-03-29
Hello, try following the instructions on **_[this howto]("http://ubuntuforums.org/showthread.php?t=257684")_**
I installed the ATI X1400 drivers from the repos(easy way) try following STEP by STEP, it took me a while to get it going because i forgot one thing or another.
It worked for me!

Hope this helps :wink:

---

### Post by raim1312 on 2007-03-30
well i followed those instructions completely and still no direct rendering and fglrxinfo gives me this:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


any other ideas? also ive seen that how to before i just didnt know the 8.28 driver supported my card but after a little research apparently it does. the only drivers ive ever been able to get working are 8.24, 8.25, and 8.26.

---

