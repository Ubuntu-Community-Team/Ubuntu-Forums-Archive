---
title: "temp overflow"
date: 2008-08-23
forum: General Help
---

### Post by capo1949 on 2008-08-23
Solved, thx to all responders

Hi All
I have a problem, as you can see my overflow is 100%, can someone please advise how I can clear the contents to obtain 0%. Alarms this prob when i try to run xp on vmware, also my printer wont work.

Hardy distro being used

Thx your help 
Graham
.
graham@study-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            233162484 136932148  84479596  62% /
varrun                 1557336       156   1557180   1% /var/run
varlock                1557336         0   1557336   0% /var/lock
udev                   1557336        76   1557260   1% /dev
devshm                 1557336        12   1557324   1% /dev/shm
overflow                  1024      1024         0 100% /tmp
gvfs-fuse-daemon     233162484 136932148  84479596  62% /home/graham/.gvfs
tmpfs                  1557336     39776   1517560   3% /lib/modules/2.6.24-21-generic/volatile
/dev/sdb1            208025648  63543052 144482596  31% /media/DRV4_VOL1
graham@study-desktop:~$

---

### Post by LateNiteTV on 2008-08-23
```
rm -rfi /tmp
```

---

### Post by capo1949 on 2008-08-23
Hi
I want to remove the contents of temp not the temp file?
Graham

---

### Post by LateNiteTV on 2008-08-23
i know. that will remove the contents.

---

### Post by jpkotta on 2008-08-23
That is a small /tmp.  I would recommend moving it over to the / filesystem.  I've never seen "overflow", what is it?

---

### Post by capo1949 on 2008-08-24
Solved, thx to all responders

---

