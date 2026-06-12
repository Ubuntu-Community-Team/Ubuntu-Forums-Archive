---
title: "Reinstalling Wubi"
date: 2008-10-03
forum: General Help
---

### Post by ESE150 on 2008-10-03
I've got a N00bish question:
If I uninstall the version of Ubuntu that I installed through Wubi (through the option to uninstall, using the Wubi installer that I downloaded from Internet), then install again the same version (using the Wubi method again), will any configuration of Ubuntu from my previous installed version remain? If so, how can I get rid of it so I can make a clean new installation of the OS?

I'm asking this because when I first installed Ubuntu, I had problems trying to make my modem work, and tried many method that I read online to install and configure it from the terminal, but ended up messing up some parts of the configuration of Ubuntu, like cursor not working anymore after rebooting. So I reinstalled Ubuntu by using Wubi, and while my mouse works correctly now, I've got some problems that I didn't have the first time I installed Ubuntu: it doesn't open the GUI automatically, but rather I've got to press Ctrl+Alt+Del for it to appear. And while not in GUI mode, it keeps giving me the message "[UEAGLE-ATM] requesting firmware ueagle-atm/DSPep.bin failed with error -2", which unless I'm mistaken, was a message that started appearing in my previous installation of Ubuntu when I tried installing the firmware for the modem.

---

### Post by ago on 2008-10-03
When you uninstall all wubi files (/ubuntu) are deleted. If you want to keep the settings, copy /ubuntu/disk/root.disk somewhere else. After the installation of the new system you will be able to mount the old root.disk with mount -o loop and access any file in there.

---

