---
title: "Copying backed up partitions to new RAID 0 setup"
date: 2010-05-25
forum: Hardware
---

### Post by cj.surrusco on 2010-05-25
I am trying to copy my OS's (Ubuntu, Xubuntu, Kubuntu and XP), which are backed up on a data drive, to a new RAID 0 setup that I configured using my motherboard's BIOS. The BIOS uses a tool called Option ROM. I have already used that tool to setup two 80GB drives in RAID 0.

The tool says that the setup is functunal, but when I boot up the GParted CD, it shows the two disks seperately and does not recognize the RAID setup.

Any suggestions? 
Thanks in advance

---

### Post by cj.surrusco on 2010-05-25
bump

---

### Post by cj.surrusco on 2010-05-26
bump again

---

### Post by tgalati4 on 2010-05-26
I don't think gparted can handle BIOS RAID drives.  Do you have any operating system installed on this system?  Or are you trying to restore an image to your clean RAID drives?

---

### Post by cj.surrusco on 2010-05-26
I am simply trying to copy over partitions that have been copied to a data drive. There aren't any images, I planned on just copying them back over and reinstalling the bootloader. 

I made progress with RAID 1, which I'm going to try to use instead of RAID 0. The GParted live CD recognized the RAID 1 setup, and I was able to copy my Ubuntu Partition. I booted up the Ubuntu live CD to install Grub, but it is showing up as two separate drives again.

---

