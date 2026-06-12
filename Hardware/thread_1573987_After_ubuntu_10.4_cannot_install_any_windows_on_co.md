---
title: "After ubuntu 10.4 cannot install any windows on compaq presario V5026EA"
date: 2010-09-13
forum: Hardware
---

### Post by silentlt on 2010-09-13
Hello, i have laptop Compaq Presario V5026EA and i used ubuntu Linux  about six months. And now i want to install windows as second OS, but i  have problam with any Microsoft OS... When i am booting from install CD,  after all hardware scaning (example windows xp, before license  agreement page) mine laptop full shuting down. After that i tried to  boot with Herien's boot cd MINI XP . it's work fine. but i cannot  install any windows who  i tried (xp, vista, seven).

please help me...

---

### Post by quixote on 2010-09-15
A bootloader is like a mini-operating system that tells the computer how to boot the real one, like Ubuntu or Windows.  Ubuntu uses grub (Grand Unified Bootloader :)), which can see all sorts of OSes.  Windows uses its own which sees only Windows.

So, assuming you had a good install of Windows, it would write its own bootloader to the machine, and it would look like you'd lost your Ubuntu.  Then you have to go fix grub, which will show both OSes. (More info [here]("https://help.ubuntu.com/community/Grub2") and [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").)

I'm not sure why your laptop would shut down just because you boot from an Windows install CD.  Unless this is some new Microsoft thing ... :?, but that doesn't seem likely.  Are you sure the CD is okay?  Have you tried booting with it in another machine?

---

