---
title: "Kernel Panic with R8192 + skype"
date: 2012-10-18
forum: Hardware
---

### Post by draucia on 2012-10-18
I previously made a thread with the same problem, but this time I have found the culprit.

I have the DWA-130C dlink wireless card. It did not work out of the box, I had to create a folder in /lib/firmware called "RTL8192U" and put the 3 files for the firmware in there. After I rebooted, it worked.

But the problem is, whenever I open skype with this card plugged in (and the module loaded), it gives me a kernel panic. Here is the picture:

[IMG]http://i.imgur.com/TTzwL.jpg[/IMG]

I tried unplugging the wireless card before booting (so it doesn't load the module), and skype doesn't crash. What could I do here?

I have ubuntu 12.10 64 bit (this happened on 12.04 too). This doesn't happen on Linux Mint 13 KDE 64-bit (only other distro I've tested).

Thanks for reading. :)

---

### Post by draucia on 2012-10-20
Still having this issue. Should I try the windows XP version of these drivers with ndiswrapper and see if it makes a difference? They are also called rtl8192u, though.

---

### Post by draucia on 2012-10-22
Tried the XP drivers, but it didn't work. Since nobody seems to have an answer for this, does anybody know how I can log what happens when I open skype (right before kernel panic)? It happens instantly and no terminal output is posted or anything.

---

### Post by mrbean71 on 2012-11-29
PLease Check the bug i've filed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1083299](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1083299)
add information about your kernel panic, i have the same happening on my PC. you can attach the picture of your screen there.

---

