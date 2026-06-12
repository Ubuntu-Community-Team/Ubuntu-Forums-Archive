---
title: "Problem with a nvidia optimus graphics card"
date: 2016-01-03
forum: Hardware
---

### Post by onlinecloud1 on 2016-01-03
I have a asus 2in1 with a nvidia geforce 940m with optimus support. 
When i installed the proprietary drivers and bumblebee Xorg would no longer start.
I found out that when I deleted xorg.conf and used "startx /usr/bin/gnome-session --session=ubuntu", Xorg would start again.
But everytime I started lightdm xorg.conf got overridden, and it caused xorg to have a invalid config file.
I found a solution on the internet, I had to add "nogpumanager" to /etc/default/grub then delete the invalid xorg.conf.
I dont know why it did that.

---

