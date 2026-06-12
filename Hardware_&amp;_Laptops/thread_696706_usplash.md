---
title: "usplash"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by fmezzo on 2008-02-14
Hi,
I have a problem with start up:
during startup I don't see Ubuntu logo adn I don't see progres bar, but I seew black screen.
May be I should configure usplash, but I don't know what I should make.

Can you help me.

Thanks

---

### Post by Existentialist on 2008-02-14
The max resolution of the splash screen is 1024x768 which you may have to manually set.  You can edit:
/etc/usplash.conf

and add:

xres=1024
yres=768

save and reboot.

Another thing you could try is adding vga=791 to the end of the kernel line in
/boot/grub/menu.lst if the first option doesn't work.

---

### Post by mmpatels on 2008-02-17
Hi all

im new to linux so ur help vl b highly appreciated. i dont know if im in correct forum or not. if not kindly guide me to correct one

when i try to run command

gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-mine.c -o usplash-mine.o

i get a error

usplash-mine.c:1: error: expected '=', ',', ';', 'asm' or '___attribute__' before 'opening'

can some 1 help me to solve this problem

thx
mmp

---

