---
title: "Getting Splashy to work with fresh Kubuntu/Ubuntu 5.04 install"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by itatabitovski on 2005-04-28
Hello everybody,

I've just installed Kubuntu and i am trying to get Splashy to work. However before loading the kernel it says that i am passing wrong video parameters, What do i need to set in order to have framebuffer support and be able to use splashy??

- Splashy and dependencies are installed
- I am using the kernel from the install - not recompiled
- in grub - menu.lst in the kernel line i have
```
kernel          /vmlinuz-2.6.10-5-386 root=/dev/hda3 ro quiet splash vga=0x316 video=vesafb:mtrr,ywrap,1024x768-32@60
```

---

### Post by Goshawk on 2005-04-28
Your menu.lst looks good.
Please see where you got the packages.

---

