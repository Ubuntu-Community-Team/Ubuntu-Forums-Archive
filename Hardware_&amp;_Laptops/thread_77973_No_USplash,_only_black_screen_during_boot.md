---
title: "No USplash, only black screen during boot"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by teevee on 2005-10-17
I installed 5.04 on a relative's laptop, an older Gericom Webboy P3 with 850Mhz. Now upgraded to 5.10, but there's no USPlash when I boot, only a black screen. Now I already did a search and got a couple of hits. Removing a vga= boot parameter seems to solve it for many, but I don't have such a parameter in my /boot/grub/menu.lst.

When I installed 5.04 from CD, I had to start it with "linux debian-installer/framebuffer=false" (see [bug 2385](http://bugzilla.ubuntu.com/show_bug.cgi?id=2385)), otherwise it would just show a blue/black screen instead of the installation interface. Guess my USplash problem is also related to this. What can I do?

---

### Post by teevee on 2005-10-18
Please?

---

### Post by recmar on 2005-10-18
Had the same problem when installing 5.10 on my acer laptop. Couldn't find the solution so I decided to reintall system (few other bugs appeared). During new installation I decided to partition disk in a different way. I created seperate /boot partition with ext2 file system on it and boot splash appeard! I know it sounds insane but... it worked for me:D

---

### Post by mlomker on 2005-10-18
[QUOTE=teevee]Please?[/QUOTE]

It didn't work for me on an updgrade, either.  I've since done a format/reinstall and it's now fine.  I'm not sure what the answer is, though.

---

### Post by teevee on 2005-10-18
Thanks for answers.

But Windows-style reinstalling is not an option. Just disabled it now. But if someone knows something that could help to get it working, let me know. :)

---

