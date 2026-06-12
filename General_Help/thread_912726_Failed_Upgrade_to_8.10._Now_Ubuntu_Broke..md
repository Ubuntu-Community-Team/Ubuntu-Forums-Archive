---
title: "Failed Upgrade to 8.10. Now Ubuntu Broke."
date: 2008-09-07
forum: General Help
---

### Post by ivansf92 on 2008-09-07
At first, I tried upgrading my computer to the alpha 5 using the upgrade-manager -d command (I think, it was on the ubuntu page). Anyways, once it started installing the updates, it just closed. And when I re-ran the command and tried upgrading again, it closed again.

So I restarted my computer and after the boot-up screen, it says it is in low-graphics mode and cannot detect anything, and has three boxes: configure, something else, and cancel I think. But the problem is, I can't move my mouse and the keyboard doesn't work.

Help please... =[

---

### Post by Neo_The_User on 2008-09-07
My updater didn't close but my video was completely messed up. I had enough of those low-graphics mode errors back when I used nVIDIA and I re-install my system as soon as I get them. I always found it to be quicker doing a fresh re-install. I recommend going back to 8.04 and wait until the video gets all caught up before switching to Ubuntu 8.10 again. I hope you didn't have several gigs of critical / important files on your hard drive. If so, you can use a spare HDD if you have one and then back your files up on it before re-installing your system. If you understand the driver / video bugs in Ubuntu inside and out, it should take you about 10 - 20 minutes getting your video back the way it was (not sure if it is fixable in 8.10) but if you really need to stick with 8.10 and don't fully understand how all the weird video is, you can try installing Envy (you need to know if you have an nVIDIA or ATi graphics card) and if Envy can't install the driver because of some xorg problem, try downgrading the xorg version back to 7.3 or lower. If Envy can't install the driver due to your kernel being too new or something like that, use git and download the kernel source from whatever previous release you were using.

hardy: git://kernel.ubuntu.com/ubuntu/ubuntu-hardy.git
gutsy: git://kernel.ubuntu.com/ubuntu/ubuntu-gutsy.git
feisty: git://kernel.ubuntu.com/ubuntu/ubuntu-feisty.git
edgy: git://kernel.ubuntu.com/ubuntu/ubuntu-edgy.git
dapper: git://kernel.ubuntu.com/ubuntu/ubuntu-dapper.git

or you can go to kernel.org and download the 2.4 or 2.2 kernel source and see if Envy can install the driver module in the kernel in the previous version. Hope that helps.

---

