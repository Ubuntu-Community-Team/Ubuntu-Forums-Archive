---
title: "Help w/ Ubuntu 10.10, GeForce 6200 PCI Card Installation, and Intel Onboard Graphics"
date: 2011-02-28
forum: Hardware
---

### Post by Starbuck13 on 2011-02-28
I'm kind of a casual user but I'm totally lost on how to go about getting this fixed. I've looked online and in the forums, but there's so much conflicting advice that nothing I try seems to work.

I've got an Intel motherboard with on board Intel graphics and I'm trying to install a GeForce 6200 512 MB PCI card. I go thru the installation and updates, and then I install the drivers that Ubuntu recommends, and when I reboot, it just hangs. If I restart from there, I get a xterm console. I'm running a fresh install of 10.10 with an active internet connection. 

Can anyone give me a hand or point me to a step by step tutorial? I'm willing to post whatever info anyone needs on here to help me figure this out. Thanks!

---

### Post by zenwalker on 2011-02-28
What is the default enabled Graphics chip in the BIOS. Based on that, your OS shall work with it. And when you switch over to one graphics card to another, your system wont be able to work with it right over. Because the Xorg.conf will be configured to work with intel driver (if already intel card was enabled before) and not with nvidia if you enable it. 

So change the xorg.conf file driver to nvidia manually (boot into console mode) and then reboot. 

On the flip side, i dont know if the driver what you have downloaded works fine with the chip. May be you can get it off the nvidia site itself.

---

### Post by Starbuck13 on 2011-02-28
> **zenwalker said:**
> What is the default enabled Graphics chip in the BIOS. Based on that, your OS shall work with it. And when you switch over to one graphics card to another, your system wont be able to work with it right over. Because the Xorg.conf will be configured to work with intel driver (if already intel card was enabled before) and not with nvidia if you enable it. 

So change the xorg.conf file driver to nvidia manually (boot into console mode) and then reboot. 

On the flip side, i dont know if the driver what you have downloaded works fine with the chip. May be you can get it off the nvidia site itself.
I did switch over the BIOS to PCI Graphics after I did the nvidia driver install. But it caused it to sort of freak out totally---bad resolution, weird things about USB devices not loading, etc, etc.

How would I go about installing the drivers manually from the site?

---

