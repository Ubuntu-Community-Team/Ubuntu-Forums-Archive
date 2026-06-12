---
title: "What happens after a Wubi Installation is uninstalled?"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2009-11-04
I would like to know what changes happen in the computer after a wubi installation of ubuntu has been uninstalled...

---

### Post by mobilediesel on 2009-11-04
> **mahela007 said:**
> I would like to know what changes happen in the computer after a wubi installation of ubuntu has been uninstalled...

Since wubi really only installs a folder in the Windows filesystem the only thing that happens when you uninstall is you'll have some disk space back.

The **boot.ini** file may still have an entry for Ubuntu but it can be edited to remove mention of Ubuntu.

---

### Post by mahela007 on 2009-11-05
So it doesn't format any partitions when it is intalled?

---

### Post by Bunnybugs on 2009-11-05
No, it makes a file that Ubuntu will see as your filesystem, you windows partitions can be mounted in ubuntu....

If you remove Wubi, all that happens is removing the whole booting stuff that Wubi created, your BIOS won recognize ubuntu anymore, so it won't ask you to boot ubuntu, or another OS...

(I've started using Ubuntu with Wubi, but the clean install works much better, Widdows slows your computer down, and it's a viral bucket)

---

### Post by jmarcoscano on 2010-03-14
hello i have a problem after uninstalling wubi from windows7, i assigned to the instalation 30GB, but after uninstallation i cant recover my 30 GB...!!!!

---

### Post by garvinrick4 on 2010-03-14
Just make sure you uninstall from Wubi folder in C: and not using Add and Remove programs. You can look in 7's bootmanager to see if there is a wubi left by Code: bcdedit at command line in Windows.
It can be deleted simply if it is left after uninstall. Google there are a lot of links to deleting in bcdedit.

To check filesystem in Windows:

Run chkdsk /f

hit y

reboot

Next:

defrag your Windows a time or two.

Next:

Check in C: in Windows right next to Users and make sure Ubuntu folder is gone.

All these are just maintinance if uninstalled correctly there should be no Wubi folder left and or problem with disk space.
But they should be run.

---

### Post by Mark Phelps on 2010-03-14
If you don't want to mess with hand-editing the BCD (and I can understand folks being nervous about that ...), you should download and install EasyBCD from the NeoSmart Technology forums.  Be sure to get the latest (v2 Beta bld82) version.

That will allow you to remove BCD entries by selecting them using a pulldown.

---

