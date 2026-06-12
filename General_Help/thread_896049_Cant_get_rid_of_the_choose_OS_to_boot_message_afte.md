---
title: "Cant get rid of the choose OS to boot message after live CD"
date: 2008-08-20
forum: General Help
---

### Post by iamallama on 2008-08-20
i tried the live CD to test out ubuntu and i used the option (Help me boot from cd) because even after i selected to boot from cd/dvd in bios it wouldent work.. the cd wrote some stuff and it worked. On reboot it booted into the live CD and i played around with ubuntu.  I decided i would stick to XP but whenever i boot up my computer i still get that message of which OS i want to boot Windows XP or Ubuntu and i dont know how to get rid of it

---

### Post by mb_webguy on 2008-08-20
Hrm... Do you have your Windows installation CD?  If so, boot from it.  If you choose to repair your installation, I think there's an option somewhere to repair the MBR (main boot record).  Choose that, and it *should* fix the "problem".

---

### Post by redjam on 2008-08-20
In XP, try editing your boot.ini file to remove Ubuntu from the list or at least make XP the default and set the timeout to be 0:
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

If that doesn't work, you will have to reset your Master Boot Record to what it was prior to you trying Ubuntu.

You can do this by booting with the Windows CD to enter the recovery console, then running fixmbr. Google fixmbr for more info. [http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

---

