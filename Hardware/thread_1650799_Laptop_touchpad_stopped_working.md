---
title: "Laptop touchpad stopped working"
date: 2010-12-22
forum: Hardware
---

### Post by bu3askoor on 2010-12-22
Hello,

I have been using ubuntu for a while now.  Unfortunately all of the sudden my touchpad stopped working.  When booting, the mouse cursor is stuck in the middle of the screen and cannot do anything.  Please note that it is working fine under other OS.

I would appreciate it if someone can share some hints with me.

Thanks,
Saeed

---

### Post by bu3askoor on 2010-12-22
ok i dropped back to virtual terminal using ctrl+alt+f1

 and typed :   sudo apt-get remove xserver-xorg-input-synaptics

then i installed it again

 sudo apt-get install xserver-xorg-input-synaptics

now it is working fine

---

