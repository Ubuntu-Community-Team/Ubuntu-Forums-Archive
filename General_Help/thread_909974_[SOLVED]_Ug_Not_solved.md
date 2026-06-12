---
title: "[SOLVED] Ug Not solved"
date: 2008-09-04
forum: General Help
---

### Post by wfp on 2008-09-04
Ok i posted back that this thread was solved [http://ubuntuforums.org/showthread.php?t=906179](http://ubuntuforums.org/showthread.php?t=906179)  I ran into another problem with this new partition. A coulple days back i had a failed install on this partition, tried to install kubuntu on a dual boot with ubuntu system freezed half way through. I have received some great help here and was able to mount the new partition and give my self owner ship. But there seems to be about 350Mbs on that partiton thats left from the failed install and the partiton is not showing up in home or desktop thou it's listed under system monitor the dircetory that is locked on that partiton is lost&found. Was hopeing there was a way to delete the rest of that failed install on that partiton, would just reinstall but my cdrom is out. So it seems like thats what left of that failed install on that partiton is blocking me some how from useing the new partiton.

---

### Post by wfp on 2008-09-04
Ok have everything working now the onley thing i would like to do is get a dev/sda7 drive icon on my desk top i went into gconf-editor and checked add new volume label to desktop but nothing is showing up.

---

### Post by Linteg on 2008-09-04
I believe the drive has to be mounted in /media/something in order for its icon to show up on the desktop.

---

### Post by wfp on 2008-09-07
Hey thank's i just made a new dir /media/mountingpoint and gedit my etc/fstab . So i just removed mnt from /mnt/mountingpoint and replaced it with /media/mountingpoint and rebooted and have new 24.9 media drive icon on desktop. Thanks to both of you learning new stuff everyday. smeagol

---

