---
title: "Considerations for Windows reinstall"
date: 2008-07-11
forum: General Help
---

### Post by BritTim on 2008-07-11
While my Ubuntu 8.04 installed using Wubi is running fine (installed on my "D" drive) the Windows XP I am using is corrupted and I want to reinstall it. I would prefer to save the necessary Wubi files, format and reinstall Windows XP on the "C" drive and copy the Wubi files back.

Can anyone confirm definitely:
[LIST=1]
[*]this should work, except that it will no longer be possible to uninstall Ubuntu through Windows 'Add and Remove Programs';
[*]the files to be copied and restored are: boot.ini, wubildr and wubildr.mbr;
[*]there is nothing else important that I must do that I am unaware of.
[/LIST]

Thank you in advance for your help.

---

### Post by VirtualSandBox on 2008-07-19
Well, this reply may not help you :(, but it might help you to know that the uninstall will in any case not work. I have installed 8.0.4.1 and tried uninstalling. 

The uninstaller is not working, it seems to be a stub that is still being worked on. 

I am not sure if anybody had been successful in uninstalling... :confused:

---

### Post by ago on 2008-07-21
backup the ubuntu directory, run wubi.exe again, then replace the ubuntu dir with the one you backed up. You might need to change the UUID of the root disk in c:\ubuntu\disks\boot\grub\menu.lst as that may change. And you will also be able to uninstall.

---

