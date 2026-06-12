---
title: "how to install built in webcam?"
date: 2010-09-07
forum: Hardware
---

### Post by xycris on 2010-09-07
hi,

i have an asus f9fseries with a builtin camera. it works fine on windows but it can't be installed properly in 10.04. is there a way for me to install this?

it is detected when using lsusb. here is the output;

xycris@xycris-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

thank you in advance for the help.

---

### Post by AlexZaim on 2010-09-07
1)Upgrade to the latest kernel.
2)Try to find the drivers on the net.
3)If you need a software to help you to activate it, try either skype or cheese.

---

### Post by xycris on 2010-09-09
> **AlexZaim said:**
> 1)Upgrade to the latest kernel.
2)Try to find the drivers on the net.
3)If you need a software to help you to activate it, try either skype or cheese.

hi AlexZaim,

i have already tried using the latest mandriva (2010) live cd who uses a later kernel than what ubuntu is using but to no avail.

i have hunches that the installed web cam on the laptop is not uvm designed.

i have searched that it is possible to use non uvm webcam in linux but i don't know how to do it with the model i currently have.

upgrading to the latest kernel (though the 2.6.35 is stable) is dangerous for my end for i don't know what will happen when it fails. it might be costly too (not just monetary terms)

thanks for the help. i greatly appreciated it.

God bless :)

---

