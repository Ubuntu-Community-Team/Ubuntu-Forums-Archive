---
title: "[SOLVED] how to set up textual and colored boot?"
date: 2008-09-16
forum: General Help
---

### Post by jakonj on 2008-09-16
Hello,

I used gentoo once as live disk and i found out that it has really nice boot colors.

My point: i can uninstall usplash but how can i set up some fancy font and colors for text boot up screen? I dont know what to search on google so i can not find sollution to this by myself...

Like debian: when you install netinstall disc and then build up desktop (done it soooooo many times) without usplash and other splash screens. Just simple text but that text was uglly so how can i change colors? I can search on net for gentoo config but i really dont know what to search for.

Please help
tnx

---

### Post by Idefix82 on 2008-09-16
Go to /boot/grub and open the file menu.lst. There is a line commented, which will make the boot text colorful. You can simply remove the comments. It is explained in the file itself. Just be careful with the file, don't change anything that you don't completely understand!

---

### Post by Nepherte on 2008-09-16
> **Idefix82 said:**
> Go to /boot/grub and open the file menu.lst. There is a line commented, which will make the boot text colorful. You can simply remove the comments. It is explained in the file itself. Just be careful with the file, don't change anything that you don't completely understand!
As far as I know, you can only set the colors of the grub menu and not the colors of the boot process in that file. By the way, you don't have to uninstall Usplash if you want to see a textual boot. You can just remove the 'splash' option in the kernel line in /boot/grub/menu.lst. This is an example using my menu.lst file:
```
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=6dcb96a9-cf73-4441-857e-839fccb522a8 ro quiet **splash**
initrd          /boot/initrd.img-2.6.24-19-generic
quiet
```
Change it to:
```
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=6dcb96a9-cf73-4441-857e-839fccb522a8 ro quiet
initrd          /boot/initrd.img-2.6.24-19-generic
quiet
```

To get a textual boot, see this tutorial: [http://ubuntuforums.org/showthread.php?t=192675](http://ubuntuforums.org/showthread.php?t=192675)

---

### Post by jakonj on 2008-09-16
i tried to uncomment that line in grub but there is no change (btw my timeout is 1s and i cant see grub by default :> ). I will try to mess with lsb init. That is the answer to my problem (but i dont know color codes for that script so tnx for link to tutorial).
Tnx

---

