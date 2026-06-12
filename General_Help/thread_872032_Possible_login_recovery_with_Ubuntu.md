---
title: "Possible login recovery with Ubuntu?"
date: 2008-07-27
forum: General Help
---

### Post by LinuxNewb092 on 2008-07-27
Hello guys, I just booted up my Ubuntu machine and I was wondering if there was anyway to get my password because I forgot it. The reason being that I havent used this machine in 2 months or so. Is there a safe mode to boot into or some other way to get it back?

---

### Post by scragar on 2008-07-27
You can't get it back, but you can change it.

Turn your computer on.
Press ESC at the grub prompt.
Press **e** for edit.
Highlight the line that begins kernel ........., press **e**
Go to the very end of the line, add ```
rw init=/bin/bash
```
Press enter, then press **b** to boot your system.
Your system will boot up to a password less root shell.
**CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!**
Type in ```
passwd **<username>**
```replacing <username> with your username.
Set your password.
Type in reboot.
Press enter

---

