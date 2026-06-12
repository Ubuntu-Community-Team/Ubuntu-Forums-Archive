---
title: "Dual boot w/server 2008: always runs scandisk"
date: 2008-08-17
forum: General Help
---

### Post by Sudrien on 2008-08-17
Note: It's not like I can find a single licence for Windows server 2008 to purchase, so this issue may go a away in... about 100 days. 


Setting up dual boot went rather smoothly, even starting with 8.04 server install - except for the fact that I didn't set up a mount point in /etc/fstab.

So, I install ntfs-3g, and put this entry in fstab... 

```
# /dev/hda1
UUID=B6CA34BCCA347B27 /media/win2008 fuse.ntfs  auto 0 0
```

Which works, until I reboot into win2008. Scandisk wants to run, and even if I let it go, I need another full reboot to win2008 for the drive to mount again in linux. A viscious cycle.

I can only think it has to do with the ntfs "enhancements" win2008 has- and somthing in a security patch, as I didn't have this issue until maybe a month ago.

Anybody have ideas of how to avoid scandisk?

-Sud.

---

### Post by zagnut48219 on 2008-09-30
I don't think it has to do with the "enhancements" you speak of. I could be quite wrong though.

I'm having a similar problem. I'm running a triple boot (Win2k sp4, XP sp2 and Gutsy) setup. Logging into XP, no problems. Logging into Gutsy, no problem. Log into win2k and chkdsk wants to scan the XP partition. I let it 1 time long ago and it completely wiped out my XP partition. Needless to say, I make sure to cancel the scan within the allotted time to ensure that doesn't happen again. Then, after being in win2k, restart to log into XP and win2k has set a dirty flag on the XP partition. So XP's chkdsk wants to run to check it's partition upon boot. That one I always let run.
To further complicate my setup, this was originally a dual boot with 2k and XP. I got a new hdd and cloned it using acronis true image, leaving the partitions the same size. With new available space of around 90gig, I then installed Gutsy and GRUB. I fear that this has something to do with my problem, but I'm not sure.

BTW, I just noticed where your from. If you look up the 5 digits in my username, you'll see the same. Cept I moved this past March to Iowa. How things going back there in the big D? Is the state's economy still falling apart? And thank god they got Kwami out of office finally. Took 'em long enough.

---

### Post by dcstar on 2008-09-30
> **Sudrien said:**
> Note: It's not like I can find a single licence for Windows server 2008 to purchase, so this issue may go a away in... about 100 days. 


Setting up dual boot went rather smoothly, even starting with 8.04 server install - except for the fact that I didn't set up a mount point in /etc/fstab.

So, I install ntfs-3g, and put this entry in fstab... 

```
# /dev/hda1
UUID=B6CA34BCCA347B27 /media/win2008 fuse.ntfs  auto 0 0
```

Which works, until I reboot into win2008. Scandisk wants to run, and even if I let it go, I need another full reboot to win2008 for the drive to mount again in linux. A viscious cycle.

I can only think it has to do with the ntfs "enhancements" win2008 has- and somthing in a security patch, as I didn't have this issue until maybe a month ago.

Anybody have ideas of how to avoid scandisk?

-Sud.
Remove the fstab entry so Linux does NOT mount the NTFS partition.

Unless you absolutely need to access the Windows system partition, don't mount it as I seem to recall that there is a bug in unmounting NTFS partitions.

---

