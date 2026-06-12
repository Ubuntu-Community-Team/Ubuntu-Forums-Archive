---
title: "VBE doesn't support wide-resloutions on analog LCD"
date: 2010-05-22
forum: Hardware
---

### Post by inso_741 on 2010-05-22
'vbeinfo' doesn't list wide screen resolutions when on my monitor. I've an 19" analog(vga) lcd.(has a native resolution of 1440x900)
however when I connect another lcd(my friend's) digitally(dvi) everythings works fine...'vbeinfo'
lists its native resolution...what can I do to solve this issue?
I'm using lucid 64-bit.....which I think doesn't matter because it is a vesa framebuffer issue...

---

### Post by inso_741 on 2010-05-23
bump...:confused:

---

### Post by dino99 on 2010-05-23
if you have a xorg.conf, remove it, kernel 32 used have many issues too, so maybe try 31 or 33 kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/)

---

### Post by inso_741 on 2010-05-23
as far as I know vesa bios extensions are loaded before the kernel...so I don't think its a kernel issue and it has nothing to do with xorg.conf

to be precise I have the issue with the resolution of grub's boot menu which is drawn using vesa framebuffer (before I select which kernel to boot with!!!)

---

