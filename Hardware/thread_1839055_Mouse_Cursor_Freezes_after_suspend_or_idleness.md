---
title: "Mouse Cursor Freezes after suspend or idleness"
date: 2011-09-04
forum: Hardware
---

### Post by vgoonjur on 2011-09-04
I have an Advent Laptop. I ve found that if my Laptop remains idle for a while or if I suspend it, the mouse cursor will be frozen in the middle of the screen. Please, can anyone tell me what to do. Thanks!

---

### Post by Toz on 2011-09-05
What model laptop? Is it an external mouse or a touchpad?

A couple of options to try:

1. Kernel paramater **atkbd.reset** ([http://ubuntuforums.org/showpost.php?p=10796261&postcount=11]("http://ubuntuforums.org/showpost.php?p=10796261&postcount=11"))

2. Kernel paramater **i8042.nomux** ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86820/comments/9]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86820/comments/9"))

Info on how to test kernel paramaters: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")

---

