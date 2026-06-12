---
title: "SysRq key not working on Lenovo R60e"
date: 2009-06-29
forum: Hardware
---

### Post by michaelc.nash on 2009-06-29
Hi everyone.

I had to help a colleague reboot another Linux machine earlier, which lead me to discover this magic SysRq key business. I was told that doing:

Alt+SysRq+R
         +E
         +I
         +S
         +U
         +B

would reboot a machine reasonably safely.

I have tried it in both GNOME and Xfce, and replaced Alt with Ctrl and Fn keys and cannot get it work.

I'm using Intrepid and my machine is a Lenovo R60e (UK flavour, in case the different keyboard layouts affect this.)

---

### Post by xaber1488 on 2009-08-30
Hi there! You have to check some things before. First of all, you must check /boot/config-<your-kernel-version>-generic and see if the line "CONFIG_MAGIC_SYSRQ" is set to "y". If not, you must recompile your kernel setting it to "y".
If "y" is set, the following step is to check with vi or nano or pico and so on if the file /proc/sys/kernel/sysrq is contains the value "1". If not, you must run at evrey reboot "sudo sysctl -w kernel.sysrq=1" (there also is a command to set the file permanently to 1 but now I don't remember it. You can't manually modify the file, because it contains a runtime value).
If yoy meet these requirements, then you should be able to run sysrq combos!
I hope I helped you!

---

