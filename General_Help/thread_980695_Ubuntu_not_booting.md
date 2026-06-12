---
title: "Ubuntu not booting"
date: 2008-11-13
forum: General Help
---

### Post by atcevik on 2008-11-13
Hello,

I am a newbie having trouble booting. The system was booting fine, but after some updates and a reset, the booting could not be completed, the error message is

Target filesystem doesnt have /sbin/init
...
/bin/sh: can't access tty; job control turned off

One of the problems is, the cpu is not a standard one, and the device is a thin client, which has storage on compact flash and no cd rom. I have usb access. The chipset is via eden.

The system has busybox running on it.

su does not work, nor most of the commands, just does not recognize, I am able to run just the busybox commands.

After the startup fails, I have a root directory in which I can see my original files, so yes, the system does see the cf. The files in it are read only.

looking at the fstab file, I see that it is empty, only has the #UNCONFIGURED FSTAB FOR BASE SYSTEM statement, also is the backup fstab.

Thus, what I guess is I need is to reconstruct the fstab, which should be far from standart, as there is a compact flash involved, manually setting it may not work. 

Do you have any suggestions ?

---

