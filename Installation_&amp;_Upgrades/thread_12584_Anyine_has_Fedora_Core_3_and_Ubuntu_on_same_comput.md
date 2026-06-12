---
title: "Anyine has Fedora Core 3 and Ubuntu on same computer?"
date: 2005-01-25
forum: Installation &amp; Upgrades
---

### Post by coolbreeze on 2005-01-25
I installed FC3 and then installed Ubuntu.  Ub didn't load Fedora in grub so i have to do it manually.  

gedit /boot/grub/menu.lst

Then I add the new entry. Here's what I added but it's not working:

title Fedora Core, kernel 2.6.9-1.667 (on /dev/hdb1)
root (hd1,0)
kernel /boot/vmlinuz-2.6.9-1.667 root=/dev/hdb1 ro single
initrd /boot/initrd-2.6.9-1.667.img
savedefault
boot

Grub does now give me a choice to boot Fedora and it looks like the kernel loads. But it says it can't find the initrd file. So it looks like I have the wrong file name. Someone please help! I am stuck!  Help!!!

---

### Post by shmonkey on 2005-01-25
I would boot into Ubuntu then mount the fedora partition to check the filename.

---

### Post by ckr on 2005-01-25
I am also attempting to do the same thing, and having problems too.  Your problem seems unrelated however.

First off, what is your hard drive situation?  Do you have one drive for both?  Did you create a separate boot partition for Fedora?

Brian

---

### Post by h4d on 2005-01-26
I'm dual booting Fedora Core 3 and Ubuntu. Here is my /boot/grub/menu.lst
```

title Fedora Core (2.6.10-1.741_FC3)
       root (hd0,0)
       kernel /boot/vmlinuz-2.6.10-1.741_FC3 ro root=LABEL=/1 rhgb quiet
       initrd /boot/initrd-2.6.10-1.741_FC3.img



title           Ubuntu, kernel 2.6.8.1-4-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.8.1-4-386
savedefault
boot

title           Ubuntu, kernel 2.6.8.1-4-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.8.1-4-386
savedefault
boot

title           Ubuntu, kernel 2.6.8.1-3-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title           Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title           Memory test
root            (hd1,0)
kernel          /boot/memtest86+.bin

```

After updating ubuntu's kernel, this file was modified, so make sure you make a backup of this file before doing so.
As you can see, I have each distro on a separate hard drive...

---

