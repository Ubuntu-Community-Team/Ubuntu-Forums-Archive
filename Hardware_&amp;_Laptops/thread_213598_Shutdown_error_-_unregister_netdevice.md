---
title: "Shutdown error - unregister_netdevice"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by jmvbxx on 2006-07-11
The full message is:

*[17201502.456000]unregister_netdevice: waiting for eth1 to become free. Usage count = 1*

The message then repeats itself with only the numbers changing.

My computer is a Dell Inspiron 9300 laptop and my eth1 is my built-in wireless adapter.


Any held is greatly appreciated!!!

---

### Post by noneofthem on 2006-07-28
I have got the exact same problem...

Please, anyone help us here. This is really annoying. Only started yesterday. Didn´t install any new software or anything else except Ubuntu updates as usual.

THanks

Amir

---

### Post by chris86wm on 2006-07-31
I have the same problem with my Inspiron 6000 :(

---

### Post by chrismyers on 2006-08-02
> **jmvbxx said:**
> The full message is:

*[17201502.456000]unregister_netdevice: waiting for eth1 to become free. Usage count = 1*

The message then repeats itself with only the numbers changing.

My computer is a Dell Inspiron 9300 laptop and my eth1 is my built-in wireless adapter.


Any held is greatly appreciated!!!

Same here with my Medion MD95564 with fitted Intel Wireless 2200BG.

It was working fine with dapper until recently. I suspect an update has broken it. Boo hoo :-({|=

---

### Post by chrismyers on 2006-08-02
I think I've found a fix. I believe it's a current Kernel problem.

My problematic kernel is 2.6.15-26-386

To test it I selected the previous kernel (2.6.15-23-386) at boot time & shut down a few times. This appears to work.

To make it permanent I commented out the problematic kernel in the boot menu. Run this to edit:

sudo gedit /boot/grub/menu.lst

Put a # at the begining of each line you want to comment out.

I hope this helps.

---

### Post by chrismyers on 2006-08-02
-

---

