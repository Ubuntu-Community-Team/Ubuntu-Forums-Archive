---
title: "usb problem"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by dannyp32 on 2009-05-03
hello i am new to linux and i want to try out ubuntu but i dont want my changes to be erased every time i reboot
 
i did a persistent install on a 2 gb usb using the tool in the live cd
i have already checked my live cd for error and it says that there are no errors
 
when the usb persistent install tool finished i rebooted using the usb ( the live cd was no longer inside)
the ubuntu menu that says
"try without any changes to your computer
install ubuntu 
check for defects" (something like that) 
this menu comes up fine 
 
but the problem starts when i choose try without any changes to your computer
after a little while of loading the screen turns black and i get exactly this:
 
[ 2.572013] ata3: softreset failed (device not ready)
[ 3.408016] ata4: softreset failed (device not ready)
 
modprobe: could not load /lib/modules/2.6.28-11-generic/
modules.dep: no such fie or directory
 
Loading please wait...
 
Busybox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in 
shell (ash)
 
enter 'help' for a list of built in commands
 
(initramfs)_
---------------------------------------------------------------------------------
i am pretty sure the problem is not my usb drive because i was able to install ubuntu 8.10 and use it by doing the same method
before i installed i tried formatting my usb drive to fat32 and fat
please help me out i really want this work because i love ubuntu 9.04 but i cant install it on my computer due to other issues
i forgot to mention i have tried reformatting it and installin it again with the same cd but i got the same problem
i also used the method in pendrivelinux.com but i got an error aswell ( i dont remember if it was exactly the same but i think it was)
does it matter if the cd is amd64 or i386 because mine is amd64 and my computer has a amd athlon x 2 5200 processor so i know it supports it
thanks

---

