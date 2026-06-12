---
title: "mount doesn't recognize 'ntfs-3g' as a filesystem."
date: 2008-10-16
forum: General Help
---

### Post by Keatonguy on 2008-10-16
So, I'm trying to get my ntfs partition to mount. I drop it in /etc/fstab, and under file system I give ntfs. It mounts, but it's read-only. So I google up some help, up comes a thread on this forum that tells me to use ntfs-3g. So I check apt-get, says I already have it, and the thread tells me to pass ntfs-3g as the fs, so I try that, and as the title suggests, mount doesn't recognize it.

For the record, it does have XP on it, and mount doesn't give me the dirty shutdown error when I try to mount with the file system set as ntfs.

---

### Post by shawnrgr on 2008-10-17
Please post command used and output, also output of 'sudo fdisk -l'

---

### Post by Yellow Pasque on 2008-10-17
You can try the program "ntfs-config", which is supposedly a GTK GUI that makes this sort of thing easy.

---

### Post by Keatonguy on 2008-10-17
ntfs-config gave the same result, it didn't think 3g was there. I reinstalled it after that, rebooted, and now, for whatever reason, it's working.

Thanks for the suggestions anyway.

---

