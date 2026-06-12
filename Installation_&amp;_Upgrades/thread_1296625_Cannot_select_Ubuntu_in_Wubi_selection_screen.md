---
title: "Cannot select Ubuntu in Wubi selection screen"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by xLelouchxx on 2009-10-20
So I was interested in trying out Ubuntu since I'm a Mac user who cannot afford a Mac and Windows is just awful. So I downloaded Wubi since I just wanted to try it, but the problem is, when I get to the selection screen, I am not able to scroll through the list. Anyone have any ideas? I am using XP Home Edition 32-Bit.

---

### Post by tommcd on 2009-10-21
I have never used Wubi so I have no experience with it. But perhaps this tutorial from the Ubuntu wiki will help:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Also, be sure to defragment your Windows partition before installing Ubuntu with Wubi.
Remember, Wubi is not meant for long term linux installations. If you try Ubuntu and decide that you like it you should install Ubuntu the real way, to a dedicated partition on your hard drive. 
Here is a good beginner site for Ubuntu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
There is a Wubi section on that site also.

And welcome to the Ubuntu forums!

---

### Post by raprap30 on 2009-10-21
Please clarify which selection screen you are talking aout, the installation screen in Windows. when you click the Wubi.exe, or you sucessfully installed it and when you reboot you do not see the boot entry "Ubuntu" at the bootloader.

---

### Post by Mark Phelps on 2009-10-21
Take a look at the boot.ini file in your XP partition.  It should have an entry for XP and a second entry for Ubuntu. This provides the menu you see when you start up the machine that allows you to select either XP or Ubuntu. If it has no entry for Ubuntu, the Wubi install failed.

---

