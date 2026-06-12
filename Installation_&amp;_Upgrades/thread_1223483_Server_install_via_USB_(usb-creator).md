---
title: "Server install via USB (usb-creator)"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by wfvoogd on 2009-07-26
Hi,

Has anybody have any luck with installing the ubuntu-server distribution via usb? I made a bootable usb-stick (ubuntu-9.04-server-amd64.iso), using usb-creator. That worked very well and he stick also booted my intel atom based little server. But when it came to the instalation process itself, i got stuck on the third step, where the installation proces wants to mount the cd-rom. Since there is no cd-rom player in the server, that is doomed to fail. Searching on the internet and in launchpad i found that this was supposedly fixed by usb-creator specifying the boot options 'cdrom-detect/try-usb=true'. I checked syslinux.cfg and the boot option are there, but still i have no luck installing :(

Anybody had similar problems and more importantly were you able to fix them and if so how?

Any tips and pointers are greatly appreciated,

cheers,

Willem

---

### Post by phnhat1984 on 2009-07-26
Use iso image of Ubuntu alternatives CD to build with usb-creator, instead of desktop or server

---

### Post by wfvoogd on 2009-07-26
Ah ok I will try that then. I did manage to get the desktop version installed, since that installer never tried to do anything with a cdrom, but i really would like the server version. I hope the alternate cd will leave me with a choice; ah well i will soon find out :)

thank you very much for the swift reply!

cheers,

Willem

---

### Post by wfvoogd on 2009-07-26
Well the alternate cd installer also installs the desktop edition, wthout any choice to select the server edition... :(

I find it really strange that the live and alternate cd let me install ubuntu, be it desktop edition, fine, while the server edition keeps nagging me for a cd-rom device :(

I guess I'm going to check the differences in server and alternate edition, preseed wise etc, in order to let the alternate cd install the server edition packages. Meanwhile any more tips are still very welcome! 

cheers,

Willem

---

### Post by wfvoogd on 2009-07-26
Okay, it seems I got it now, what I did was;
- use usb-creator to create a bootable usb stick from the alternate cd; 
- copy the contents of the /preseed/ubuntu-server.seed (from the server cd) to the /preseed/ubuntu.seed (on the usb), commenting out the original contents. 
- boot the server from the usb 

now it asked me if i needed mail servers etc, so i guess it acts as a server cd. 

cheers,

Willem

---

