---
title: "Problem in recovering ubuntu"
date: 2008-10-17
forum: General Help
---

### Post by arvind.laddu on 2008-10-17
Recovering Ubuntu after installing windows
I am not able to recover my ubuntu bcos of this error plz help...




grub> find /boot/grub/stage1
(hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

---

### Post by shawnrgr on 2008-10-19
Its always best to install Ubuntu after windows, not the other way around. Windows wrote over you mbr. 

fix it ;) [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

