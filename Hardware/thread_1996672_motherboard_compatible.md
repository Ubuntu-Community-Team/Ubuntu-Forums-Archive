---
title: "motherboard compatible"
date: 2012-06-04
forum: Hardware
---

### Post by KG4UJD on 2012-06-04
I am wanting to build a new sys using the ASUS M5A99X will I have any issues with the uefi bios

---

### Post by inashdeen on 2012-06-04
what is uefi bios by the way? MOOD : curious.

---

### Post by oldfred on 2012-06-04
Lots of users are having fun with the new UEFI/BIOS installer. Where fun means issues to be resolved. :)

You also then get into gpt partitioning as UEFI uses gpt partitioning instead of the 30 year old MBR(msdos) partitioning scheme. 

Windows only boots from gpt partitioned drives with UEFI. gpt is only required then with Windows & UEFI or with drives over 2TB, but is often recommended for new systems.

Is system going to be dual boot. Do you want UEFI/gpt or BIOS/MBR? And if only Ubuntu you can also have BIOS/gpt which is what I currently have.

Those that have successfully installed formated partition in advance. And both Windows & Ubuntu when booted with UEFI offer two choices - one UEFI and the other BIOS, legacy or some similar name depending on brand of UEFI.

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

GUIDE: (U)EFI installation Also full install post *52 superfreak
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)

---

