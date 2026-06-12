---
title: "Power and buttons issues"
date: 2012-03-14
forum: Hardware
---

### Post by yogie.pratama on 2012-03-14
Hi, need you`re help please!

i`ve just upgraded 11.04 to 11.10 in my laptop. before upgrade , no buttons or power issues at all. but when i the upgrade finished, i discovered:
1. my button power doesn`t work, to shutdown (before upgrade worked perfectly)

2. brightness button doesn`t work (fn+f9 or fn+f8), so i used Screen in system setting

3. when i close the lid, it doesn`t suspend and the standby ombination button (fn+f3) doesn`t work either.

Any idea?
Thx b4.

My laptop
axioo zetta mlm, with clevo motherboard
(maybe none of you ever heard this laptop)

---

### Post by yogie.pratama on 2012-03-21
Guys, guys :p finally i mended it.
 i reckon the problem came from the kernel. so the point is, changing the kernel to the version that best suited with your computer, since my ubuntu keep the previous version, so i just change it by modifying the grub bootloader. since my previous kernel in ubuntu 11.04 worked well, almost.

i replace the latest kernel with the latest or best suited previous kernel version. but keep the latest version that installed with ubuntu 11.10 in Previous Version in grub menu. but you can still use the 11.10 features or look

but, i think this just work, if your ubuntu was upgraded, no fresh install, because there isn`t any previous version of kernel if you install the 11.10 from the scratch.

hope it might help.
correct me if there is mistake.

---

