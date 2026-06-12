---
title: "How can i eliminate wireless as cause for freezing?"
date: 2009-11-15
forum: Hardware
---

### Post by Andreas1 on 2009-11-15
Hi,

i keep getting these random [freezes]("http://ubuntuforums.org/showthread.php?t=1309015"), and in Debian, depending on whether wireless is turned on, i get kerneloops error messages. so i thought i'd disable the wireless completely and see if ubuntu still freezes? how do i do that, is the wireless driver part of the kernel?

(the thing is, in ubuntu, unlike debian, the wireless hardware is automatically turned on when rebooting. btw, device is an Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection)

---

### Post by confused_user on 2009-11-15
unloading the kernel module will do that.

i dont know which module your 3945ABG uses.

try a modprobe -l | grep 3945ABG and see what comes out, you should see a file called nameofmodule.ko

once you have found it type sudo modprobe -r nameofmodule.ko to remove it

---

### Post by Andreas1 on 2009-11-15
> **confused_user said:**
> unloading the kernel module will do that.

i dont know which module your 3945ABG uses.

try a modprobe -l | grep 3945ABG and see what comes out, you should see a file called nameofmodule.ko

once you have found it type sudo modprobe -r nameofmodule.ko to remove it

thanks!

just to be sure - i can easily undo that later, right?

---

### Post by confused_user on 2009-11-15
yeah, you can either reboot and it will (should) just reload the kernel module as usual or you can do it manually with 

sudo modprobe -i nameofkernelmodule.ko

man modprobe for all the options

dont worry, it wont cock it up

---

