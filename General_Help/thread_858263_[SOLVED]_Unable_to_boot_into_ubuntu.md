---
title: "[SOLVED] Unable to boot into ubuntu"
date: 2008-07-13
forum: General Help
---

### Post by alexlaban on 2008-07-13
Ok everything have worked fine before but suddenly today when I should boot into ubuntu it didn't work.
Everything is as normal until after the loading screen when this text appear
```
 BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter "help" for a list of built in commands.

(initramfs) [   44.158559] sd 8:0:0:0: [sdb] Assuming drive cache: write through 
[   44.158559] sd 8:0:0:0: [sdb] Assuming drive cache: write through
```

Them ot staus that way about 10-15 minutes and after that the screen turn black. I've restarted serval of times but always the same error. Anyone know what it may be?

---

### Post by ago on 2008-07-14
Probably windows was not shutdown cleanly. Boot into windows, run chkdsk /r on the drive where you installed ubuntu, reboot cleanly and try again

---

### Post by alexlaban on 2008-07-15
Thank you  for your help. This time the problem solved itself but now I know what to do if it would happen again. Sorry for my bad English, I'm Swedish. But I hope that you can understand what I write.

---

### Post by ago on 2008-07-15
Often booting into windows and rebooting cleanly is sufficient, since windows runs a program at boot that clears the dirty flag. We do not have an equivalent in linux (yet), hence the need to fix it from windows.

---

