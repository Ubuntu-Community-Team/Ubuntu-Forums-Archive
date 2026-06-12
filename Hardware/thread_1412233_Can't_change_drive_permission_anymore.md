---
title: "Can't change drive permission anymore"
date: 2010-02-20
forum: Hardware
---

### Post by wattaman on 2010-02-20
Hi! I want to use rsnapshot to make backups and I can't because the second driver is read-only (so it say).
I'm using webmin to administer the server and when trying to change the directories permissions it doesn't let me - again, read-only.
It was not like this before and I have no idea why now is read only and before it wasn't. I have this in my fstab file:
> proc            /proc           proc    defaults        0       0
/dev/sda1  /  ext3  grpquota,suid,dev,defaults,usrquota,exec  0  1
/dev/sda2	none            swap    sw              0       0
/dev/sdb1  /HDD2  ext3  defaults  0  0
/dev/sdb2  swap  swap  defaults  0  0
I want to backup a folder on the sda1 to sdb1 (don't know for sure if I need a swap on sdb but I created one, anyway).
Please note that I've tried this: [http://ubuntuforums.org/showthread.php?t=1264741](http://ubuntuforums.org/showthread.php?t=1264741) but it didn't worked.
As an ultimate solution, I'm thinking to just format the sdb again, but don't remember how I did it the first time (must be the age :)).
Either way, any help would be appreciated.

BTW, this is what I got from rspanshot:
> Output from command /usr/bin/rsnapshot daily ..

----------------------------------------------------------------------------
rsnapshot encountered an error! The program was invoked with these options:
/usr/bin/rsnapshot daily 
----------------------------------------------------------------------------
ERROR: Could not mkpath("/HDD2/daily.0/", 0, 0755);

---

### Post by wattaman on 2010-02-21
I've also noticed this message in my Webmin panel, under the partition I'm trying to change: 
> This partition cannot be changed as it is currently in use or configured for use.

---

### Post by wattaman on 2010-03-01
Ok. I'm still fighting this issue.
So, I've formatted the drive sdb drive and it worked a while. I also use rsnapshot to store the backups of sda on sdb, only for the websites on the server. But, unfortunately, it stopped again.
Now is the same as before, "**This partition cannot be changed as it is currently in use or configured for use.**" appears in the webmin configuration when I access the partition on the sdb drive and I got the error that the drive is read-only whenever I try to create new folders/files etc. Of course, rsnapshot stopped working, too, the last span was 1 week before, though is programmed to run daily.
I have no idea who is usinbg the sdb drive (if any process); I'm looking at the running processes but don't see nothing that can help me. The drive is set to mount as read-write, by the way, not as read-only.
Any ideas, please?
BTW, dunno if this matters, I'm using the df command to chech the used space and got 45G used on the sdb and 65G used on sda, but in the webmin system information page I see 138G used space (even if is calculated for both drives, is still almost double)

---

