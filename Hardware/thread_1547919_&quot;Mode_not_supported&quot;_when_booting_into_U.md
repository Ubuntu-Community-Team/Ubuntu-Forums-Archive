---
title: "&quot;Mode not supported&quot; when booting into Ubuntu"
date: 2010-08-07
forum: Hardware
---

### Post by Private Bob4 on 2010-08-07
Hello everyone, I just burned Ubuntu into a disk, and whenever I try to boot into Ubuntu, my monitor says "Mode Not Supported." My  monitor is a Samsung TV. MY graphics card is a Radeon 9800. I've got a Compaq Evo.

---

### Post by Man_Beach on 2010-08-18
I used to get this with 8.10 - it turned out to be due to the splash screen and I got round it by disabling the splash screen in Grub by adding nosplash to the menu.lst options i.e. 
#defoptions = quiet nosplash

Unfortunately I've no idea how to disable the splash screen with Grub2. Perhaps a bit of Googling or checking the Grub 2 manual to see how to do it might help?

---

