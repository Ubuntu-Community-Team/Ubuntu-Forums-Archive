---
title: "Can't resume from hibernate Hardy/Intrepid"
date: 2008-11-05
forum: Hardware
---

### Post by fireoptic on 2008-11-05
Ok, here's the issue.

I installed to a USB hard drive with my internal SATA disconnected. after I changed my /etc/fstab and /boot/grub/menu.lst to make the USB sdb and the internal sda I was able to boot and everything except the hibernate works.

Let me be clearer. I can hibernate but I can't resume it just goes to the normal boot process. I think it has something to do with a config file not pointing to sdb for the swap.


any help would be greatly appreciated. thanks in advance.

edit< upgrade to intrepid solved problem

---

