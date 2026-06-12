---
title: "Ideapad 330s AMD Ryzen 5 2500u screen won't dim or brighten, Ubuntu 18.04.3 lts"
date: 2020-01-23
forum: Hardware
---

### Post by rb8623 on 2020-01-23
I am having an issue with the display not dimming or brightening with either the keyboard or setting controls. Not sure what is going on, but I have researched similar issues with other machines. Most of them say to edit the grub file, in particular the "quiet splash" option. However, I have already had to manipulate that to resolve a hanging boot issue where the screen froze prior to the login screen by adding nomodeset. The following are my settings in grub:
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""

Has anyone else had any issues with this? Any help is much appreciated, thanks in advance!

---

### Post by rb8623 on 2020-02-06
Following up, still no solution.
Anyone else experience this?

---

### Post by CelticWarrior on 2020-02-06
'nomodeset' is to be used as a temporary workaround ONLY. With it pretty much nothing works because its purpose is to give a very limited generic display without using the graphics drivers.

If you have a Nvidia graphics card you need to install the Nvidia drivers (open Additional Drivers for that) and then remove 'nomodeset'.

---

### Post by CatKiller on 2020-02-06
One thing that might help with part of it is to use a newer version of Mesa. There are a range of different PPAs for different levels of newness. I don't use AMD graphics myself, but I understand that [this one](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa) is popular with those that do. Nomodeset is a nuclear option that inhibits a lot of graphical stuff, since the open source stack uses kernel modesetting and that option turns it off. It's possible that option's interfering with your brightness setting, or it might be something else.

---

### Post by mastablasta on 2020-02-07
or use the newer kernel found in 19.10

the 18.04.4 LTS with new kernel is not out yet i believe. it is planned for February: [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

the older kernel in 18.04.03 should work ok, however you have a mobile chip and these got proper support later. so if  possible i would say go with newer kernel. drivers in linux are usually part of kernel.

another option is the mentioned PPA. definitely worth a shot as well.

---

