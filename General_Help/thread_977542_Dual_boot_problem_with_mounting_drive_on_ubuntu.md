---
title: "Dual boot problem with mounting drive on ubuntu"
date: 2008-11-10
forum: General Help
---

### Post by XFrame on 2008-11-10
Hello. I have dual boot on my laptop, windows xp sp2 and ubuntu 8.10.

Say i'm working on windows xp. If i shut down windows xp, and restart the computer, then i get to grub, chose ubuntu, and everything works fine. Problem is if i hibernate windows, instead of shutting it down. If i enter ubuntu with windows in hibernate mode (next time i go to windows, all my programs will be opened), it wont mount the ntfs drives. This is very annoying, since i often need to hibernate windows, and then if i go to ubuntu i cant listen to music that i have on windows partiticion, for example.

Is there any way to fix this?

Many thanks in advance

---

### Post by caljohnsmith on 2008-11-10
What error do you get when trying to mount the NTFS partition? You can also check:
```
dmesg | tail
```
And that will probably tell you the error. You might try "ntfsfix" on the partition:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdXY
```
And replace sdXY with your NTFS partition, like sdb2 for example. Let me know if that makes any difference.

---

### Post by prshah on 2008-11-10
> **XFrame said:**
> Problem is if i hibernate windows, instead of shutting it down.it wont mount the ntfs drives. This is very annoying, since i often need to hibernate windows, 

Unfortunately there's no way out. Ubuntu will not automount drives that contain hibernation information.

---

### Post by XFrame on 2008-11-10
Thank you both for your time... So it seems there is no way out. :(
Best Regards, XFrame

---

