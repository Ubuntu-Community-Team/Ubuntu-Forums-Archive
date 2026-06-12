---
title: "Bios Raid 1 Confussed!"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by waloshin on 2009-07-15
Hi i have an Asus M3n78vm-hdmi board. i went into bios and stup raid 1. I have the alternate cd and when i loaded the installtion I first saw a screen that said One or more drives containing Serial Ata Raid configurations have een found. Do you want to activate these Raid devices? Then after that I got:

 Serial ata raid nvidia_ffihedcj () - 160gb Linux device-mapper. 

Does this mean if I install it on this Nvidia Bios Raid, it will run as Raid 1?

When installing the base system I got an error saying that the kernal package Linux-generic could not be installed.

---

### Post by ronparent on 2009-07-15
First, to answer your question - not necessarily. To install and run as raid you need to follow the instructions here:[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

To clarify some: nvidia_ffihedcj is what is called a symbolic link. This particular one represent the entire array. If there were any partitions on that array they would be represented by their individual symbolic links ie nvidia_ffihedcj1, nvidia_ffihedcj2, etc. These are merely hooks for ubuntu to act on the array rather that the individual componet drives. So installing ubuntu to the array followint the above HowTo will permit you to install on and run from the raid1 array.

---

