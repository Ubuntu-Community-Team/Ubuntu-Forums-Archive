---
title: "Asus ProArt XP13 (hn7306wi) and Ubuntu 24.10"
date: 2024-11-09
forum: Hardware
---

### Post by jmartini2 on 2024-11-09
Hello, 

I own the Asus ProArt XP13 (hn7306wi).

I have installed the Ubuntu 24.10,  but I'm facing the following issues:

1) Unable to put to "sleep" Ubuntu. When the notebook is put to sleep, it immediately switches on and the logon screen graphic is broken.
2) Unable to control the Backlight of the keyboard with the available menu Keyboard.

Tech specification for the mentioned notebook can be found here  [https://www.asus.com/laptops/for-creators/proart/proart-px13-hn7306/techspec/](https://www.asus.com/laptops/for-creators/proart/proart-px13-hn7306/techspec/)

Have you been facing such kind of issues with a same notebook or similar hardware?

Any help is appreciated.

Thank you

JM

---

### Post by jmartini2 on 2024-11-10
Hello,

while trying several configurations it seems that I found the proper settings for the suspend/resume issue, so I would like to share my findings with you

1) Modify /etc/modprobe.d/nvidia-graphics-drivers-kms.conf and add the following lines:

# Added by JM - fix NVIDIA suspend and graphical issue after resume
options nvidia NVreg_PreserveVideoMemoryAllocations=1
options nvidia NVreg_TemporaryFilePath=/var/tmp

Hope this helps others with the same hardware Asus ProArt XP13 (hn7306wi).

---

