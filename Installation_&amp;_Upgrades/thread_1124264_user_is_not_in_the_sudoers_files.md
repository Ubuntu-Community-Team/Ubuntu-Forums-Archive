---
title: "user is not in the sudoers files"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by lcs81 on 2009-04-13
It has been few time, not sure what happen, during log in, key in the password and come out a message user is not in the suoders files. It dont allow me to install or uninstall anything that required administrative right. This time is even worse, for ubuntu 8.04 32 bits, suddenly after restart, the GUI is gone and become command prompt just like server version only......

---

### Post by Aubergines on 2009-04-13
That doesn't sound good, unless you've done something totally weird in your install I'd check if the disk is burnt properly and that your machine is actually stable.

---

### Post by drs305 on 2009-04-13
At the command prompt, try to add yourself back to the admin group with: 
```

adduser *yourusername* admin

```
Example: adduser john admin

If it won't run like that, add "sudo" and try again although this most likely won't work. In that case, boot to the recovery mode and run the same command again.

Select the recovery mode option from the grub menu. If you don't see the options because you have an automatic login without the grub menu display, reboot the computer. As it boots, look for the grub menu and hit ESC to reveal the menu. If you never see any indication of the grub menu, start hitting the ESC key after you hear the computer's system beep.

You probably have other issues, but getting yourself back into the admin group is something you probably will need.

---

