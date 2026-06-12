---
title: "Wireless does not connect on boot."
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by Bunnykun on 2007-07-01
I have an Inspiron e1705.  I have gotten my wireless drivers to work, and I am able to connect.  But the problem is that when Ubuntu first starts, the wireless doesn't connect automatically.  when I click on the network connect icon and connect to the network, it'll try to connect and then fail.  But, if I disable the wireless with Fn+F2 and then reenable it, Ubuntu will connect fine.    These are the instructions I followed to install my wireless drivers, I have used them successfully many times in the past.  This is the only time I had this particular problem, and i can't help but think I missed a step somewhere.  Any ideas?

[http://ubuntuforums.org/showthread.php?p=1741197#poststop](http://ubuntuforums.org/showthread.php?p=1741197#poststop)

---

### Post by Bunnykun on 2007-07-01
bump

---

### Post by Ayuthia on 2007-07-01
Do you have ndiswrapper in /etc/modules?

---

### Post by Bunnykun on 2007-07-02
Yes, it is.

---

### Post by chiklit on 2007-07-02
I have a Compaq Presario R4000 / Broadcom 4306 chip and have to do the same thing. The card appears to be enabled on boot, but it can't connect until I turn it off and on with the button on my laptop.

---

### Post by Bunnykun on 2007-07-02
Exactly as the user above describes.  This is not a major inconvenience but it does defeat the point of trying to mount network drives on boot.

---

