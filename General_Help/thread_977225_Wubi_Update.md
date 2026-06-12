---
title: "Wubi Update"
date: 2008-11-10
forum: General Help
---

### Post by bobc4012 on 2008-11-10
How can I update my current Wubi setup without "uninstalling" and "installing"? Whenever I tried to update to the next release, Wubi uninstalls everything, which results in my having to download all the applications, locate the bookmarks (to save and update - export and then import does not do a "clean import"). In other words, nothing is saved and I have to spend hours re-installing everything and re-initializing. I also have learned to save any files that I have created and then have to restore them after an "Ubuntu release update"

In the past, I tried to update from the Update Manager when informed the next release was available - click on "update to x.xx". This burned me twice. The first time I did it was a while back and running FIXBOOT and "FIXMBR" was sufficient. The second time, I lost my XP boot.ini file and also had to run CHKDSK /r (or chkdsk /p /r) in order to boot my XP system. The "update to the next release" apparently assumes that it is a dedicated Ubuntu system and changes the hard drive, even though it updated Ubuntu in the "virtual disks". Weird, - it knows about the virtual disks, but assumes an Ubuntu HD. Fortunately, it does not delete the XP directories. I can see the XP directories by running the Ubuntu CD.

---

### Post by abn91c on 2008-11-10
if you use Kubuntu, Open the Run Command dialog by pressing Alt+F2. Type kdesudo "adept_manager --dist-upgrade" in the command box and press the OK button. include the "" marks

for ubuntu do this [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
turn off desktop effects before you start or you may have problems

---

### Post by bobc4012 on 2009-07-20
> **abn91c said:**
> if you use Kubuntu, Open the Run Command dialog by pressing Alt+F2. Type kdesudo "adept_manager --dist-upgrade" in the command box and press the OK button. include the "" marks

for ubuntu do this [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
turn off desktop effects before you start or you may have problems

I did that once before and was burnt. Wubi allows you to run Ubuntu in a Windows directory. It creates virtual disks. The update procedure you referenced wipes out the MBR. It assumes that Ubuntu is on a dedicated HD. What I need to find out is how to update Ubuntu in a Wubi install on a Windows system. I do not want to partition my HD for specific reasons at this time. Maybe sometime in the future. However, there should be a way to update without uninstalling and re-installing via Wubi.  

BTW, sorry for the long delay and thanks for your effort.

---

