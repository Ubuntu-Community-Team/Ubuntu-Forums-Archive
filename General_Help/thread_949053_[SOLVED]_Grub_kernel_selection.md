---
title: "[SOLVED] Grub kernel selection"
date: 2008-10-15
forum: General Help
---

### Post by Stolea on 2008-10-15
Somewhere in the last few months I told grub to only show the .19 version kernel and WinXP for booting. I have done all the automatic updates and know that the .21 kernel is installed (todays update in fact).
I know there is somewhere in the configuration tools the ability to select more recent kernels, but can't seem to be able to find it.
Could someone please point me in the right direction
Cheers

---

### Post by drs305 on 2008-10-15
The easiest way is to install StartUp-Manager:
```
sudo apt-get install startupmanager
```

To run:
System, Administration, StartUp-Manager.
Boot Options, select the kernel you want to use.

You can also set menu timeouts, how many kernels to display, etc.

If you know what you are doing, you can edit /boot/grub/menu.lst manually as root with a text editor.

Check my signature for a tutorial on StartUp-Manager.

---

### Post by Stolea on 2008-10-15
Cheers, Your blood is worth botteling! I knew it was there somewhere, but for some reason I got the KDE version of the startupmanager installed. I have no idea where that came from. One of those mysteries of the universe :)

---

