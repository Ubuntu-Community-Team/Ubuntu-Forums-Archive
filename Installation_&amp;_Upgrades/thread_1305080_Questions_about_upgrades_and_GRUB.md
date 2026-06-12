---
title: "Questions about upgrades and GRUB"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by AcousticMinja on 2009-10-29
Hi, I currently am running a dual boot system with Windows Vista Home Basic on my first hard drive (HD0) and Ubuntu 9.04 on my other hard drive (HD1)
I am about to upgrade my Vista hard drive to Windows 7 Professional and I was wondering how I would go about doing this with my current set up. I have a couple questions, first is, would GRUB be deleted and Windows MBR be installed? Or would Grub still be there and I have to somehow add Windows 7 to the list? Would I still be able to access Ubuntu if Windows' boot loader is installed? I don't have my Windows Vista recovery disc anymore so if I had to uninstall Ubuntu, I couldn't access Vista. I'm hoping I don't have to uninstall Ubuntu because I have a lot of important files on there.

If anyone knows what I should do, please let me know how! Thanks! :)

---

### Post by dvlchd3 on 2009-10-29
Windows will ALWAYS overwrite your MBR.

Here's a guide on how to recover GRUB after installing Windows:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

