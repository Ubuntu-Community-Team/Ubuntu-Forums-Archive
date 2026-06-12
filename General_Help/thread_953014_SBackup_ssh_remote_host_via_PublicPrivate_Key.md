---
title: "SBackup: ssh remote host via Public/Private Key?"
date: 2008-10-19
forum: General Help
---

### Post by IMSargon on 2008-10-19
I would like to back up to a server that uses a password encrypted public/private key. I have no trouble accessing this server though nautilus. SBackup seems unable to connect to it, probably because I have no idea how to enter the location into the program.

I have read the documentation here:
[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite#Backup%20Destination%20on%20Remote%20machine](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite#Backup%20Destination%20on%20Remote%20machine)
and here:
[http://migas-sbackup.sourceforge.net/readme.html?PHPSESSID=42568da50a28a6d0df212819ecb60a52#M5](http://migas-sbackup.sourceforge.net/readme.html?PHPSESSID=42568da50a28a6d0df212819ecb60a52#M5)

The latter explains that one can use keys with SBackup and then explains in great detail how to create a key, but never explains how to use this setup with the program!

I'm sure someone out there knows the answer to this, or at least has some links to better documentation.

---

### Post by cariboo on 2008-10-19
Can you connect using ssh? In a terminal type:

```
ssh username@server
```

If you can connect then you have ssh setup. I use grsync to backup my home direstory to my server. I use the following to connect:

```
user@server:/home/user/backups
```

Jim

---

### Post by IMSargon on 2008-10-20
I have no problems connecting by ssh. In fact, using either ssh or "connect to server..." I can use simply "ssh servername2" to automatically use the correct username and key pair via my config file in the ".ssh" directory. However, this method does not seem to work with SBackup.

I am not familiar with grsync. Does it support incremental backups with logarithmic purging? Can it prompt for the password to the key files?

---

### Post by IMSargon on 2008-11-10
The answer to this thread:

To use a public/private key with SBackup, you need only put your private key in root's ".ssh" directory (because SBackup runs as root, not your user). If this key requires a password, you will be prompted by GNOME (This feature may be incomplete in the Intrepid version, but a patch exists: [https://bugs.launchpad.net/sbackup/+bug/290237](https://bugs.launchpad.net/sbackup/+bug/290237) )

---

