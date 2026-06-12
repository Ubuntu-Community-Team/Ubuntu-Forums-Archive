---
title: "Black Screen Again :("
date: 2010-05-04
forum: Hardware
---

### Post by samy_yusif on 2010-05-04
here what happened
1- for Ubuntu 10.04 CD 
it gives me black screen before installation , i type " nomodeset "
and i complete installation 

2- after restarting after installation system does not work at all and gave me black screen

3- i had this problem before in Ubuntu 9 when i install my graphic card so i waited for new Ubuntu but it does not work at all

description of my computer
- laptop ( Sony vaio vpccw13fx)
- nvidia graphic card <<<<<<<<<<<<<<<<

any solution????

---

### Post by ronparent on 2010-05-04
If the grub menu isn't coming up when you boot, hold down the left shift key right after the bios boot screen passes. In the grub bot menu, hit 'e' to edit on the line you want to boot to - is nomodeset present in the kernal boot line ( the line with quiet splash)? If not add it to the end of that line. Does it boot correctly now (hit <ctrl> x to boot)? If it does, then you have to add that parameter to the line in /etc/default/brub after quiet splash. This may correct your problem if nothing else is afoot.

---

### Post by samy_yusif on 2010-05-05
i do that as u say , but the problem after installation ubuntu does not work and gives me black screen  ( after computer boot and choosing ubuntu it gaves me that black screen )

---

