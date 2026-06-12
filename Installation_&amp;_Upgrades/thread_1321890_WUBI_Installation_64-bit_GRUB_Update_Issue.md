---
title: "WUBI Installation 64-bit GRUB Update Issue"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by bluejackal06 on 2009-11-10
Hello,
         I am new to Ubuntu and i wanted install it on my work laptop. Just to be safe, i installed Ubuntu 9.10 using Wubi. I chose the default options and Wubi chose the 64-bit edition on Ubuntu 9.10. Everything was running smooth for a few days. After that, the update manager showed some critical and recommended updates. I believe i saw an update to Grub in the "Recommended" section. I installed everything thats shown on the update manager.

I have the habit of closing my laptop lid and not shutting down. After the update was done i closed the lid. While opening it again, the laptop was not switching on, so i did it a hard restart (holding on the power key to shut down and switch it back on). I selected Ubuntu from the menu, and it showed some error which i cant read. Then it showed me command prompt called GNU GRUB 1.97~ Beta. I tried several commands, but cannot boot into Ubuntu.

I unistalled Ubuntu using Wubi. I like Ubuntu and want to install it on a separate partition, but after this problem i am hesitant.

Could someone shed some light on this issue?

Any help is appreciated.

---

### Post by MichealH on 2009-11-10
Your /boot/grub/menu.lst might be screwed up near or on the error can you press CTRL-ALT-F1 and to go to login on text based mode?

---

### Post by CvRudo on 2009-11-15
I can't find the file that you said, but in other forum i saw this solution but is temporally and frustrating when you see the message in the grub you need to tape>
```
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-14-generic
boot 
```
The 2.6.31-14 is the version of the kernel and the sd2 is the place where ubuntu is installed, i am a noob user if someone could give more information of the final solucion i will apreciate it.
grettings

P.D: Sorry for my english

---

