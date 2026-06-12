---
title: "Booting"
date: 2012-09-08
forum: Hardware
---

### Post by fauhid on 2012-09-08
Today i reinstalled windows 7 on my pc but actually i could find the  bootloader for ubuntu yet i had ubuntu 12.04.1 previously installed.What can i do to recover my ubuntu plus my data in it.

---

### Post by yankeeDDL on 2012-09-08
If you only need to retrieve the data, try with the liveCD first (from a USB key).
If that does not work, then try the install process (also from the LiveCD/USB) and you may get the option to restore the old partition/installation.

---

### Post by oldfred on 2012-09-08
You should just have to reinstall the grub2 boot loader to the MBR if the Ubuntu partitions are still intact.

Several alternatives:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

If you prefer a gui:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

