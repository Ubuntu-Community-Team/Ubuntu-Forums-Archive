---
title: "fstab and external hard drives"
date: 2010-06-20
forum: Hardware
---

### Post by ray field on 2010-06-20
I am not very handy setting up disks, I will admit.

I've got two external HDs, one which used to show up as SimpleDrive, the other which was labeled as EXTERNAL.  after I upgraded from Jaunty to Karmic last week I started having trouble with them, so I reconfigured the pertinent parts of fstab with /media/ext as the mount point for EXTERNAL and /media/ext2 the mount point for SimpleDrive.  they seemed to work fine for one or two reboots but now I'm having problems:

```
  
UUID=3736-3666                             /media/SD_BAK    vfat         users,defaults,umask=007,gid=1000,uid=1000,noauto  0  0  
UUID=C81C-14F1   /media/ext      vfat         defaults,user,exec,uid=1000,gid=100,umask=000 0 0  
UUID=20E87C4FE87C2566  /media/ext2    ntfs         defaults,nls=utf8,umask=000,uid=1000 0 0
```

now when I boot, EXTERNAL shows up as /media/ext, and I am able to access it through Nautilus.  however when I click on the unmounted "ext" icon on the Nautilus side panel, I get the popup
```

mount: /dev/sdc1 already mounted or /media/ext busy
mount: according to mtab, /dev/sdc1 is already mounted on /media/ext
```

on the other hand, though "ext2" shows up as mounted in Nautilus, clicking on that icon gives me a popup labeled Could not display "media/ext2"

```
Error: Error stating file '/media/ext2': Input/output error
Please select another viewer and try again.
```

the unmounted SimpleDrive icon appears in Nautilus, however when I try to click on it 

```
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /media/ext2
mount failed
```

hopefully I'm mising something obvious.

---

### Post by ray field on 2010-06-21
bump

---

### Post by dino99 on 2010-06-21
install mountmanager and set your prefs from: system admin mountmanager

---

### Post by ray field on 2010-06-21
thanks, seems to have done the trick -- I was a little skeptical, never having had much luck with pysdm, but this seems considerably better -- will know for sure after the next reboot.

an additional problem was the disk was badly in need of chkdsking, fortunately my girlfriend left her windoze netbook here...

---

