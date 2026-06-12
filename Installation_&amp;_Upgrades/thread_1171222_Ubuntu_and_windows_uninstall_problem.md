---
title: "Ubuntu and windows uninstall problem"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by domagoj91 on 2009-05-27
I have a big problem.
I am working on windows xp sp3 OS, and I've decided to try out ubuntu. I inserted live cd. and started wubi installation inside windows. In the end of installation I've got some error that access to some tmp files is denied. I closed msg down, then I started to do some stupid things. Insted of runing ubuntu uninstall i deleted ubuntu folder from hard drive... now i can't boot either windows either ubuntu. from some reason booting from cd is not option but I have access to other hard drive with windows os. so how to make my first hard drive bootable again but only windows with access from other hard drive.

When Try to boot windows i just keep geting msg that Ntdlr is missing and CTRL+ALT+DELETE to restart

sry for my language....:D

---

### Post by ajgreeny on 2009-05-27
I suspect you need to restore the windows MBR using the recovery mode from the windows install CD.  Boot to that CD, choose recovery (I can't remember how now, but it will be obvious I think) and then choose fixmbr from the options that appear.  Ignore the warning as you can't boot at the moment anyway, and when the fixmbr has finished restart, and you should then get into windows.  You can then try to clean up your hard disk properly by reinstalling ubuntu again and then uninstalling it  the right way in windows Control Panel, Add/Remove, if you don't want to keep it.

If you don't have a windows CD you may like to try installing ubuntu again, just forgetting about the MBR for now.

---

### Post by lisati on 2009-05-27
> **ajgreeny said:**
> I suspect you need to restore the windows MBR using the recovery mode from the windows install CD.  Boot to that CD, choose recovery (I can't remember how now, but it will be obvious I think) and then choose fixmbr from the options that appear.  Ignore the warning as you can't boot at the moment anyway, and when the fixmbr has finished restart, and you should then get into windows.  You can then try to clean up your hard disk properly by reinstalling ubuntu again and then uninstalling it  the right way in windows Control Panel, Add/Remove, if you don't want to keep it.

If you don't have a windows CD you may like to try installing ubuntu again, just forgetting about the MBR for now.

I might be mistaken, but I don't think Wubi touches the MBR (or shouldn't)

---

### Post by Mark Phelps on 2009-05-27
Since you claim you can't boot from CD, try pressing F8 during the boot to see if you can at least get into safe mode in XP or get an option to select System Restore.

Also, write down the error message you're getting when it won't boot.  Different messages will indicate different problems and solutions.

---

### Post by domagoj91 on 2009-05-28
ok I managed to boot recovery console but fixing MBR or boot sector dosent work i still geting message "NTDLR is missing Ctlr+Alt+Del to restart"

with f8 i am only geting options to boot from other devices. any other solutions?

regards!

---

### Post by louieb on 2009-05-28
This might help [How to fix XP when the boot files are missing - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=813628")

---

