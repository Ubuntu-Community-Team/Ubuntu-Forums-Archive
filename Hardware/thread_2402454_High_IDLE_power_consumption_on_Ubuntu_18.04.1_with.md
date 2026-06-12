---
title: "High IDLE power consumption on Ubuntu 18.04.1 with  Ryzen7 1700 and Radeon RX 570 GPU"
date: 2018-09-30
forum: Hardware
---

### Post by simone.pulcini on 2018-09-30
Hi,

I'm experiencing an abnormal power consumption while IDLE on my Ryzen 7 1700 cpu desktop with AMD Radeon RX 570 based GPU card, 16GB of DDR4 on Ubuntu 18.04.1 with the latest patches applied. I need your help to debug this issue with more details so feel free to suggest me some commands to run from the console so I can post their output here.
System in Idle mode runs between 69 to 75 watts (obtained from the plug using APC UPS). While the system is in IDLE it should run actually between 43-48 watts: this power usage is the IDLE power reached in Windows 10 as well as in Ubuntu 18.04.1 during the log-in screen. **Just after the log-in the power consumption raise up reaching the reported one when reaching idle state**.
I verified using "top" that there's no abnormal cpu activity (around 0.9%) so the CPU should reach its lower P-State correctly. I suspect the culprit should be the graphic driver (I've not installed the AMD one, I'm using the default open source driver shipped with 18.04.1). My two cents that the driver clocks the GPU GDDR5 memory to top frequencies during all the activitiies, just after tje login screen.

I'm running a fresh installation (not an upgraded one).
I've got the latest BIOS 7A32v1H installed for my MSI motherboard X370 Gaming Pro Carbon with AGESA Code 1.0.0.4C (AMD Cool & Quiet enabled). Let me know how to extract more detailed configuration details.

Help really appreciated: I will forward logs here.

Simone

---

### Post by simone.pulcini on 2018-10-07
I found a sort of workaround to greatly reduce power consumption: reduce the monitor refresh from 144hz (I've got a 144hz monitor) to 60hz reduce IDLE power consumption to 50 watt...still far from the 43-48 watt I should see. Also the bug disappear if I select Wayland as default display server instead of X.Org. I tried also to install AMDGPU driver but the issue persists. I think that X.Org is main reason for this power increase. I suspect a bug in latest HWE distributed with 18.04.1

---

