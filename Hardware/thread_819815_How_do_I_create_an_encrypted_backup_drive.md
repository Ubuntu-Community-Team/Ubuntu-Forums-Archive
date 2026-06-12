---
title: "How do I create an encrypted backup drive?"
date: 2008-06-05
forum: Hardware
---

### Post by baudelaire on 2008-06-05
Once a week, I sync a drive up with all of the most recent data on my network that I deem important for off-site backup.  For added security I would like to encrypt this drive in case it were lost/stolen.  I've looked, but can't find a straight forward way of doing this.  

Can you guys please point me in the right direction?

---

### Post by baudelaire on 2008-06-06
Any ideas?

---

### Post by Rocket2DMn on 2008-06-06
Here are a few places you can start:
[https://help.ubuntu.com/community/TruecryptHiddenVolume](https://help.ubuntu.com/community/TruecryptHiddenVolume)
[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

Good luck.

---

### Post by chmac on 2008-12-15
If you're still looking for a solution, [duplicity]("http://duplicity.nongnu.org/") might be it. Duplicity creates incremental, encrypted backups. I believe it can be [automated with ftplicity]("http://www.howtoforge.com/ftp-backups-with-duplicity-ftplicity-debian-etch").

---

### Post by BrandonBan6 on 2008-12-15
I've also had some co-workers use true-crypt
[http://www.truecrypt.org/](http://www.truecrypt.org/)

Utimaco is coming out with a Linux option, if you don't mind paying a little for it. 
I

---

### Post by chmac on 2008-12-15
TrueCrypt is a great piece of software in that it can be used on the 3 major platforms (Linux, Mac, Windows) so you can be fairly confident of decrypting your data if you have the passphrase. However, I don't believe it allows for easy remote encrypted backup. You would need to create a local TrueCrypt volume, unmount it and then back it up remotely (which can be done efficiently with rsync).

I think duplicity offers a simpler solution for easy off-site backup.

---

