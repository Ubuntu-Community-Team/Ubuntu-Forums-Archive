---
title: "Log in Problem"
date: 2008-11-18
forum: General Help
---

### Post by InvertX on 2008-11-18
Hey, every time I try and log in the screen will go blank for a second and then it takes me right back to the login screen. No matter how many times I try, The login screen will just keep refreshing. If anyone can give me some advice i would greatly appreciate it.

---

### Post by InvertX on 2008-11-18
bump

---

### Post by BennBuntu on 2008-11-18
same problem here, I can't login from terminal or gdm. I'd been changing printer settings if that could be related. If I put wrong password it says so, but with right password it just loops back to the beginning. Recovery mode loads, but don't know what could fix it.

Any ideas?

---

### Post by BennBuntu on 2008-11-18
invertX, try logging in to a terminal
Press ctrl+alt+F2 at login screen.

If you can login then you might just have to clear some space on your root partition. Doesn't solve my problem though.

---

### Post by BennBuntu on 2008-11-18
Solved for me, think related to this bug, had you been playing with samba settings? 
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/260687]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/260687")

I followed these instructions from the bug report, note this will wipe your samba (network) settings.

 
- Reboot and choose the "recovery mode" from the boot selection menu
- Choose "drop into root shell" from the recovery menu
- Execute the command: dpkg --purge libpam-smbpass

---

