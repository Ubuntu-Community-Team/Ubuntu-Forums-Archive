---
title: "Dual display using Intel HD 2000 Graphics family and Ubuntu 11.04"
date: 2012-07-02
forum: Hardware
---

### Post by arpana on 2012-07-02
Hello,
 
I have two monitors - one is HCL (1280 X 1024) and other one is GS520 ( advanced EIZO monitor of 2560 X 2048. When I connect both monitors to Intel HD 2000 graphics card ( to VGA and DVI ports respectively) system hangs. When I remove GS520 from DVI port and switch on system normally goes to Ubuntu login.
 
OS used is Ubuntu 11.04 
Now the driver used is Intel, if I switch to vesa (by editing xorg.conf) I get an error, kernel mode setting enabled , and I have to disable. But still if I connect two monitors system hangs.
 
If I run Xorg -configure (to generate xorg.conf) it shows error - No of created screens does not match number of detected devices. Because of this I have written xorg.conf which appears to be Ok. because single monitor works - only dual display (2560 X 2048 has problem). 
I want a system that supports dual display during boot, and finally xorg.conf should be OK. The display 2560 X 2048 if not supported and instead '1280X2048' for big monitor and 1280 X 1024 for small monitor is supported also no issues. Kindly help me.

---

