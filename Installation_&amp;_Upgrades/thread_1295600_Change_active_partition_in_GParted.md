---
title: "Change active partition in GParted"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by Wa1k3rTXRang3r on 2009-10-19
Right now my Windows partition is active and I also have Fedora installed with GRUB on the first sector of the boot partition.

The problem is that with Windows there is no way to boot my Fedora installation.

I was just wondering if there is anyway to change the boot partition with GRUB on to the active partition using GParted on the Ubuntu LiveCD?

---

### Post by sisco311 on 2009-10-19
you have to reinstall grub:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

---

### Post by Mark Phelps on 2009-10-20
Also, don't mess with the Active status of your MS Windows partition.  It has to be active in order to boot.

---

