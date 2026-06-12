---
title: "Rsync at shutdown"
date: 2008-11-17
forum: General Help
---

### Post by VrmpX on 2008-11-17
Hello community,

 I'm asking for a bit of help in this matter, I got the rsync script that makes backups, it works perfectly. It runs from my ~/bin/ folder and backups my Windows user profile (MyUserName/Documents, MyUserName/Pictures, /Videos, /Contacts, etc...) into /media/sda2/Users/.bak/MyBackup (inside the Windows partition called sda2).

 What I'm looking for is a way to run this script just after I decide to shutdown. I already tried this:
 I created /etc/rc.d/rc0.d/, then I copied my script and renamed it into K00STimeMachine.sh. But after I shotdown, nothing happened, since the backup also puts a text file with the last successfull day and time and it didn't change.

 Thanks in advance.
 Victor.

---

### Post by dcstar on 2008-11-18
> **VrmpX said:**
> 
.........
 What I'm looking for is a way to run this script just after I decide to shutdown. I already tried this:
 I created /etc/rc.d/rc0.d/, then I copied my script and renamed it into K00STimeMachine.sh. But after I shotdown, nothing happened, since the backup also puts a text file with the last successfull day and time and it didn't change.


Scripts that work in a user environment do not necessarily work in those other areas.

Make sure you have full paths to all binaries and the root account has permission to access everything it needs to.

Use the other existing scripts as guides on how to structure things.

---

