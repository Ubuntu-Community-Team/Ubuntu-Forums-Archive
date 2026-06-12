---
title: "unable to boot to Ubuntu, plz help"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by hangnguyen on 2009-07-10
I tried install Ubuntu 8.10 inside Windows, When I reboot have bootloader display let me choose Ubuntu, when I choose Ubuntu it restart again .

I created swap and Ext3 and install Ubuntu, everything is ok however when I reboot, no bootloader display, only windows xp boot .

Please help 

thanks for your time 

sorry about my E

---

### Post by Blacklightbulb on 2009-07-10
Wait you dual boot with Xp or what?
If so check this thread:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

You need to install grub.

---

### Post by hangnguyen on 2009-07-21
I solved my proplem . 

just boot by Ubuntu CD and type, 
>sudo grub
> grub find /boot/grub/stage1
result: (hd3,5)

root (hd3,5)

setup (hd3)
quit

thanks

---

