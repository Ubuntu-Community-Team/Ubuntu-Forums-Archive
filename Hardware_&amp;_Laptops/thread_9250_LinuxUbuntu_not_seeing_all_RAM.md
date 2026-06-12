---
title: "Linux/Ubuntu not seeing all RAM"
date: 2004-12-26
forum: Hardware &amp; Laptops
---

### Post by jknotzke on 2004-12-26
Hi,

    I have a Thinkpad A31 and Ubuntu/Linux is not seeing all the ram installed:

    jknotzke@chomsky:~ $ free -m

                  total       used       free     shared    buffers     cached
Mem:           885        280        605          0         11        128

    Yet there is 1024M installed. Windows sees it, and so does memtest.

    I have tried passing the following to the kernel from the menu.lst:

    title           Ubuntu, kernel 2.6.8.1-4-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hda2 mem=1024M ro quiet splash
initrd          /boot/initrd.img-2.6.8.1-4-386
savedefault
boot


    With no real change.

    Any ideas?
 
    Thanks

     Justin

---

### Post by Wubanga on 2004-12-27
I read in the Ubuntu wiki that the kernel included in Warty can't "see" more than 900 Mb of RAM.
You should upgrade to a new kernel.

sudo apt-get install linux-686

This is in case u r running a P4. I'm a newbie (running Ubuntu since 3 days ago) so i can't help u no more.

Good luck

---

