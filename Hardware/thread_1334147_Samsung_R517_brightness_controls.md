---
title: "Samsung R517 brightness controls"
date: 2009-11-22
forum: Hardware
---

### Post by abhi.b on 2009-11-22
Hello,

I have installed Ubuntu 9.0.4 on Samsung R517 notebook.

Brightness control does not work (Fn+Up/Down). Please let me know if anyone has a fix for it.

Has anyone tried running Ubuntu 9.0.4 on Samsung R517? How is the overall experience - does all work well? Should I consider a newer Ubuntu release?

Thanks,
Abhijit
PS: Volume control works fine (Fn+Left/Right).

---

### Post by glibey on 2010-11-05
Same problem! Anybody?

---

### Post by LexxFan on 2010-12-27
I found full instructions here for my language:[I] [forum.ubuntu.ru]("http://forum.ubuntu.ru/index.php?topic=64210.0")
[/I]You may search for somefing like it here, maybe.
**Next instructions are for 10.04 Lucid Lynx!** Do this (Of course, after the editing, you must save the changes):

**Add the model name**
> R517/R717like it already done with other models in the next 2 config.files:
> sudo gedit /lib/udev/rules.d/95-keymap.rules> sudo gedit /lib/udev/rules.d/95-keyboard-force-release.rules**Also you need to add the Voria's repository for samsung. Do this steps:**
> sudo apt-add-repository ppa:voria> sudo apt-get update && sudo apt-get upgrade> sudo apt-get install samsung-tools samsung-backlight**Edit grub config file:**
> sudo gedit /etc/default/grubYou need to edit the line like this:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"[SIZE=3]**It's very important!!! ****Don't forget to do** [/SIZE]> sudo update-grubAfter the reboot, all keys are working well, but if you have model NP-*R517*-[I]DA03 (like me), you will have to use Windows 7, because Celeron M900 is unsupported by the linux-phc. There is no way to control CPU's frequency or voltage to get normal powersave mode.
**P.S.** Sorry for my English.
**P.P.S.** Good luck ;)
[/I]

---

