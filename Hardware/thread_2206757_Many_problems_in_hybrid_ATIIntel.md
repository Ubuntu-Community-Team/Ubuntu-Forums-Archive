---
title: "Many problems in hybrid ATI/Intel"
date: 2014-02-20
forum: Hardware
---

### Post by Shishimaru on 2014-02-20
Hello everyone! I'm using Ubuntu 13.10 64bit on my HP DV7 with an ATI Mobility Radeon and an integrated Intel. I have followed many guides but I always obtain errors when I try to install proprietary drivers.

I installed all kind of drivers, repository, ATI's site, betas and so on. The last tentative was a sudo apt-get install fglrx fglrx-pxpress and then a sudo aticonfig --initial -f.
When I rebooted the system, I got the usual lowgraphic mode (it doesn't even work fine). I switched console and erased the xorg.conf file. Rebooting the system again, I got stuck in LightDM pretending to insert my password, but it was totally useless. GDM doesn't work since I got bootloop for 15 minutes or more, erasing Xauthority causes my system to give me black screen. Removing fglrx is the only solution to revert the situation. I really need your help.

---

### Post by Shishimaru on 2014-02-21
Anyone?

---

### Post by Mark Phelps on 2014-02-21
Sorry, but Hybrid/Switchable graphics is a serious problem in Linux due to the lack of specialized drivers.

If you want to read up on the details, see the link: [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355]("http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355")

---

### Post by Shishimaru on 2014-02-21
OK, I will try this guide too. I hope it's good for Ubuntu 13.10 too since it has newer packages.

---

