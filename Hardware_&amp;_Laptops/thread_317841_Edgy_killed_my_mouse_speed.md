---
title: "Edgy killed my mouse speed"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by jcrnan on 2006-12-13
I just updated to edgy and now my touchpad mouse moved horribly slow, almost unusable. Any suggestions? The speed is on full in the mouse settings, but taking it up and down doesnt seem to affect anything at all.

---

### Post by maxamillion on 2006-12-13
This link is about slackware, but its all linux and thus ... same tools apply and xset is installed by default. 

[http://www.linuxforums.org/forum/slackware-linux-help/22672-setting-mouse-speed-slack-xorg-xset-slow-mouse.html](http://www.linuxforums.org/forum/slackware-linux-help/22672-setting-mouse-speed-slack-xorg-xset-slow-mouse.html)

/me

---

### Post by jcrnan on 2006-12-13
chaning stuff in xset didnt change anything at all.

---

### Post by ruggerik on 2006-12-14
try ... on menu.lst (/boot/grub) add this option at kernel parameter 

 i8042.nomux=1

after reboot


bye
Ruggerik

---

