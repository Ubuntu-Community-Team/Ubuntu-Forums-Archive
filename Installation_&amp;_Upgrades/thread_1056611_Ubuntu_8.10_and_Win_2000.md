---
title: "Ubuntu 8.10 and Win 2000"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by vpnm_87 on 2009-01-31
I had Win 2000 and Ubuntu 7.(something) (dont remember sorry)..i installed Ubuntu 8.10 sterday and installed successfully..After rebooting and entering my username,password the screen becomes blank(with background colour of login screen) and desktop is not displayed and just hangs..My win 2000 working fine with GRUB loader

My motherboard is 845 Chipset, Intel P4 processor, no graphics card..I installed it from the Live CD..No display prob when i used the Live CD.

If anyone s willing to help and more info s needed then kindly reply me as soon as possible..

---

### Post by abn91c on 2009-01-31
> **vpnm_87 said:**
> I had Win 2000 and Ubuntu 7.(something) (dont remember sorry)..i installed Ubuntu 8.10 sterday and installed successfully..After rebooting and entering my username,password the screen becomes blank(with background colour of login screen) and desktop is not displayed and just hangs..My win 2000 working fine with GRUB loader

My motherboard is 845 Chipset, Intel P4 processor, no graphics card .

If anyone s willing to help and more info s needed then kindly reply me as soon as possible..
ctrl+alt+f1 at the prompt, then ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
sudo reboot
```

---

### Post by vpnm_87 on 2009-01-31
thanks for d quick reply..i ll try it and let u know as soon as possible..

---

### Post by vpnm_87 on 2009-02-08
damn sure this s not soon as i promised..but it worked and am able to see the desktop and work with it..

---

