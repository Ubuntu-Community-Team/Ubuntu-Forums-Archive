---
title: "Installing 8.10"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by Mhurst1 on 2008-12-11
When I try installing Ubuntu or Kubuntu 8.10 once the bar goes all the way to the right I get a blank screen and nothing happens. I also have this problem if I try upgrading from 8.04. I have an ASUS m2a-vm motherboard and a ATI raden x2400 video card. WHat could be wrong?

---

### Post by albinootje on 2008-12-11
Can you still switch to a virtual console with ctl-alt-F1 after the upgrade ? 
If so, then you can try to reconfigure X with : sudo dpkg-reconfigure -plow xserver-xorg

---

### Post by Mhurst1 on 2008-12-11
I dont have an upgrade installation anymore. I am starting from scratch.

---

