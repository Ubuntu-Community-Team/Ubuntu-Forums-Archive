---
title: "Problem with splash screen"
date: 2008-11-04
forum: General Help
---

### Post by kbloem on 2008-11-04
Hello all,

i installed the finger splash screen in ubuntu linux 8.10. Everything goes well and it shows no error messages. However when i boot linux all i see is text.

My menu.lst looks like this:
> ## ## End Default Options ##

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            eb46bce6-35e5-455f-ad44-bb5eb61661f0
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=eb46bce6-35e5-455f-ad44-bb5eb61661f0 ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.27-7-generic
boot

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            eb46bce6-35e5-455f-ad44-bb5eb61661f0
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=eb46bce6-35e5-455f-ad44-bb5eb61661f0 ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            eb46bce6-35e5-455f-ad44-bb5eb61661f0
kernel          /boot/memtest86+.bin


### END DEBIAN AUTOMAGIC KERNELS LIST


Can someone tell me what i'm doing wrong?

Thanks

---

### Post by philinux on 2008-11-04
Mine has quiet where yours has the line boot.

---

### Post by kbloem on 2008-11-07
Thanks for your reply but it doesn't work. It does nothing. Strange.....

Anyone?

---

### Post by plucky on 2008-11-07
I have the same problem and no solution,but I have found that if you remove the "quiet" from the kernel line,the system boots with the usplash and scrolling text beneath it.

With the "quiet" in the kernel line,it is a text boot only.

This is on a system that was upgraded from the 8.10 beta alternate CD and with all updates applied.Haven't tried a clean install from the "release" CD as yet.


Good Luck

---

### Post by kbloem on 2008-11-10
Removing the quiet option didn't do anything. The strange thing is that the original works fine. It's also the only one working.....

---

