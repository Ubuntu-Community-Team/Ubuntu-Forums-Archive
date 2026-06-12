---
title: "can't write to cd AND admin pass doesn't work"
date: 2005-11-14
forum: General Help
---

### Post by joelus on 2005-11-14
I'm putting both these problems together because, although they may be unrelated, they seemed to happen at the same time. I have windows98 on one partition, but cannot boot it due to some corrupt file or other. I install Kubuntu 5.1 on free space (had old version of mandrake there before). All's well. I want to backup my music (on the windows partition) onto cd before formatting the whole thing. Kubuntu can't see Windows directory. I go to the administration settings, hard disks and mount points, and see windows is mounted but is disabled. details on this screen are greyed out and disabled. So I click on the 'Administration' button, it asks me for my password, which I give, and then am able to enable windows. Great so far. Start K3b, put in blank cd, write some music! Fantasic, it works!

Put in another blank cd, try to write more music to it and get the following error:
mount: block device /dev/hdb is write-protected, mounting read-only 
(sorry, this is from memory, so might not be exact)
So I can't write to cd anymore. Try more discs, no joy. 
Restart the computer. Once again Windows is not there.
Go to Settings, click the  hard disks and mount points, and see windows is mounted but is disabled. Details on this settings screen are greyed out and disabled. So I click on the 'Administration' button, it asks me for my password, which I give - it ACCEPTS the password, but everything is still greyed out and disabled as if I hadn't put a password in.
:confused: 
So now, I can't access the windows directory and I can't mount cdRW except as read only!!
So frustrated! What can I do please? Aside from losing my music, throwing out kubuntu and loading XP!

---

### Post by mlomker on 2005-11-14
You don't want to mount CDRW discs before burning them...K3B will handle that.  I doubt that /dev/hdb is your cdrom drive...more likely the hard disk.  If you can't boot windows then that may very well be because the disk is corrupt and you need to run checkdisk on it...Ubuntu won't be able to use it any more than Windows could.

Some of the graphical tools just don't work and others can be launched from the Run Command line:  **kdesu systemsettings** or **kdesu kcontrol**.

Post the output of **sudo fdisk -l**.  You probably just need to run **sudo fsck.vfat /dev/hdb** but we'll know for sure if you post the fdisk output.

---

