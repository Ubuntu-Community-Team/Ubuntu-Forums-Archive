---
title: "lilo script for Ubuntu"
date: 2005-01-07
forum: Installation &amp; Upgrades
---

### Post by luckyxxx on 2005-01-07
I am running Xandros and Ubuntu but the ubuntu script is missing in my lilo.conf file. I have been trying to write the script myself

image=/vmlinuz
label=ubuntu
vga=0xf04
root=/dev/hda2
read-only

but have had only limited success. I have been able to at least have lilo list ubuntu in the menu but it won't boot up. I have tried inserting "initred=/boot/inetrd-2.6.8.1-3-386 or 3-386.img" and various renditions of this but nothing seems to work. I have been at this now 2 days reading lots of mans and now I ask for help. Hopefully one of you can be of help. Do you know the proper Ubuntu script to use to edit my lilo.conf file? Your help would be greatly appreciated. I have tried my best but its just not good enough.

---

