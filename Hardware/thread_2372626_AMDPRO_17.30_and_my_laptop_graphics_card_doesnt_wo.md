---
title: "AMDPRO 17.30 and my laptop graphics card doesnt work on Ubuntu 16.04"
date: 2017-09-27
forum: Hardware
---

### Post by eldarfarseer on 2017-09-27
Hello everyone i am aware this is a popular topic and many people have the same problem as i have, but when i try apply the solutions i read they don't seem to fit to my problem, so here is my problem :

I recently bought a dell Inspiron 5567 with an r7 graphics card ```
 lspci | grep Display 

01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265] (rev c3)
```.

I have installed the AMDPRO 17.30(or i think i have) ```
 dpkg -l amdgpu-pro
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  amdgpu-pro     17.30-465504 amd64        Meta package to install amdgpu Pr
``` 

and on its release notes its says that its supports my graphics card [http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx)

After the drivers were installed i got in a login loop which i solved with the help of this community, but the problem is that when i go to System Settings on the Details tab i see the Intel® HD Graphics 620 (Kabylake GT2) as the default graphics card.

The questions are, did i install the drivers correctly? If yes why doesn't Ubuntu uses the AMD card as default since the drivers were installed, and finally how can i make it work?

P.S. I have read that downgrading to Ubuntu 14.04 is a possible solution but with the 17.30 drivers more AMD cards became compatible with Ubuntu 16,04, and i wanted to ask the community for a possible solution before downgrading to 14.04.

Thank you in advance.

---

