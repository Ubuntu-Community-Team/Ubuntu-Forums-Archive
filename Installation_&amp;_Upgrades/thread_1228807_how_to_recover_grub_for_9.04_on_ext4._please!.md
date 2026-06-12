---
title: "how to recover grub for 9.04 on ext4. please!"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by tenmoi on 2009-08-01
I dual boot ubuntu 9.04 (on ext4) and debian lenny (on ext3). 
Yesterday I reinstalled grub as follows
root (hdx) (containing debian lenny)
setup (hd0) (which contains both ubuntu and lenny)

and now I cannot boot into ubuntu because "grub error 15 file not found"

I booted into lenny and reinstall grub from there but "find /boot/grub/stage2" cannot find ubuntu stage2, which I think is due to ubuntu being on ext4.

How can I reinstall grub to boot ubuntu? 

Please note I have always installed linux from the hard disk and so have no physical cds to boot from and unluckily I deleted the ubuntu iso file to save space:(

Many thx in advance.

---

### Post by Malta paul on 2009-08-01
You can use a Supergrup boot disk to restore your grub boot

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

:D

---

### Post by tenmoi on 2009-08-02
> **Malta paul said:**
> You can use a Supergrup boot disk to restore your grub boot

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

:D

THank you! I'll give it a try.

---

