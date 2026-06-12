---
title: "Automount not working with new compiled kernel (vanilla 2.6.14)"
date: 2005-11-20
forum: General Help
---

### Post by vogueboss on 2005-11-20
Hello,
I compiled my own 2.6.14 vanilla kernel. Everything is working fine exept the automount (usbkeys and cds) but I can mount them using command line.
I know I could modify /etc/fstab, but if it was possible I would rather learn how to fix the automount.
When I boot using the 2.6.12-9 ubuntu kernel, automount is working great.

thanks for your help

---

### Post by yoyoned on 2005-11-20
In the kernel config options under File Systems ther are 2 options for "Kernel automounter support".  Check if these are incuded as modules.

---

### Post by vogueboss on 2005-11-21
Hello, 
I tried to had those 2 modules and it doesn't seems to be enought.
do you guys have other ideas ?

thanks

---

