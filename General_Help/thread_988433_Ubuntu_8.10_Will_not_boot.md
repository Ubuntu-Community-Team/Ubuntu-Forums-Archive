---
title: "Ubuntu 8.10 Will not boot"
date: 2008-11-20
forum: General Help
---

### Post by rlprice on 2008-11-20
So i go to get the latest minefield build and the ISO downloads just fine. Install prompts me to reboot And the option to boot into Ubuntu is there. I select it and all i get is a black screen. No blinking cursor or anything. I am trying to dual boot this with Windows Server 2008. The wubildr files are on the C drive as they should and the Ubuntu install is on E: (my secondary hdd).  How do i get it to Boot into Ubuntu and actually load?

---

### Post by rlprice on 2008-11-21
Any help?

---

### Post by rlprice on 2008-11-21
Swapped the 80gb SATA drive out and put a 120 IDE in, somehow that fixed it.

---

### Post by n5kb on 2008-11-23
Hello,

  It sounds as if it can't find the proper partition to boot from. Try sudo gedit /boot/grub/menu.lst and look at info there. Post it here too. 

Mine is something like: Ubuntu /boot/vmlinuz
                        Windows /hd0/0

Hope this helps
Mike

---

