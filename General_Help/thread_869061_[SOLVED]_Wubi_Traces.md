---
title: "[SOLVED] Wubi Traces"
date: 2008-07-24
forum: General Help
---

### Post by diego898 on 2008-07-24
After uninstalling wubi, will any junk files or registry entries be left on my system? Will the uninstallation leave my system with NO traces of every having ubuntu? If this is not the case, what can I do to ensure that it IS the case?

Thanks for the help

---

### Post by uidb4056 on 2008-07-24
> **diego898 said:**
> After uninstalling wubi, will any junk files or registry entries be left on my system? Will the uninstallation leave my system with NO traces of every having ubuntu? If this is not the case, what can I do to ensure that it IS the case?

Thanks for the help
  Uninstalling wubi from add/remove programs will remove the bootloader file it copies in your C: modify the boot.ini to keep out the option added to boot Ubuntu and completely remove the folder it has used for the install, also it ask you if you want to backup your install or not. As far as I know no registry entries has added during the install. Your system will be clean of wubi/ubuntu after you uninstall it.

---

### Post by minhmeoke on 2008-07-25
Actually, Wubi adds one registry key at HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi so that "Ubuntu" shows up in the add/remove programs list.

In the past a very tiny minority of users still had this key after uninstallation, but I think this has been fixed in recent revisions, so you should be fine. If the key still shows up, you can always delete it with regedit or another registry editing program.

---

