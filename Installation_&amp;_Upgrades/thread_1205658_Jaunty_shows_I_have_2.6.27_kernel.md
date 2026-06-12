---
title: "Jaunty shows I have 2.6.27 kernel"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by arysar on 2009-07-06
I upgraded to Jaunty but when I boot grub shows me 2.6.27 kernel

uname -r gives me:

2.6.27-7-generic


and the grub

title Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=c55ce624-30fb-4254-895e-b8b375c563d5 ro quiet splash 
initrd /boot/initrd.img-2.6.27-7-generic

how can I upgrade the kernel?

thanks!

---

### Post by aLiEnTxC on 2009-07-06
sudo aptitude install linux-image-generic  ;-)

or sudo aptitude -f --with-recommends dist-upgrade

---

### Post by NilsE on 2009-07-06
In software sources make sure you have jaunty-security under the updates tab turn on. 

Also make sure all on the first tab are selected 

Then run update manager and you should get it.

---

### Post by arysar on 2009-07-06
Ok Thanks!

---

