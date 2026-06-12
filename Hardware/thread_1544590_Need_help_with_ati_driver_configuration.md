---
title: "Need help with ati driver configuration"
date: 2010-08-02
forum: Hardware
---

### Post by ashokmkd on 2010-08-02
Hi,
I have Dell Inspiron notebook with ATI Mobility Radeon HD 4330.
I recently installed Lucid and found that the shutting down was not regular.
The screen was always on after shutdown or restart command is given. I tried many solutions given in this site but none worked. Then I found that Ubuntu was now coming pre-installed with 3D drivers for ATI. They were not the actual fglrx drivers. So i downloaded the actual fglrx driver. Great, the shutdown problem is solved. But my catalyst control center tells that the configuration is incorrect. So i removed the preinstalled drivers.. 
To my disappointment, display was in a bad resolution and still no fglrx is detected. So i copied an xorg.conf file from another distro(PCLinuxOS) which is installed in my notebook. (I don't know much about xorg.cong)
Now i restarted and the resolution is correct and catalyst is recognizing drivers. But i cant enable the extra effects now. :( It says "The composite extension is not available". ! please help me to set the correct settings in xorg.conf..

---

### Post by ashokmkd on 2010-08-02
Solved it :) used sudo aticonfig --initial

---

