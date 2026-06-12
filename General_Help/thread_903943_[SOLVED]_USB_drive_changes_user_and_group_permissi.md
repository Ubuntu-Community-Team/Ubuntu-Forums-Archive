---
title: "[SOLVED] USB drive changes user and group permissions"
date: 2008-08-28
forum: General Help
---

### Post by Redline21 on 2008-08-28
I have a Western Digital USB drive. I copied some files and folders to it using the -p option. I looked at the drive after the copy and verified that the permissions on the folders appear to be correct. The user and group both matched the current account that I was logged into (lets say user1).

I then plugged the drive into another Ubuntu box and went to look at the permissions. I discovered that it indicated that the user and group both now matched the account that I was using on the second box (user2).

I am getting ready to migrate a bunch of files and user directories from one server to another, and I was planning on using this drive to transfer the files. Why does it appear to change the permissions based on the current user and how can I make this work? :confused:

---

### Post by mssever on 2008-08-28
What filesystem are you using?It sounds like you're using either FAT32 or NTFS. Neither filesystem supports Unix permissions, so Linux has to fake it. If you want to preserve permissions, you have to use a native *nix filesystem such as ext3.

---

### Post by Redline21 on 2008-08-28
Ah, sorry, I am using ext3. I tried fat32 but that deffinetly didn't work for permissions, so I reformanted as ext3 and now have this issue.

---

### Post by mssever on 2008-08-28
The user and group are stored internally by the uid or gid, not the username and group name. On Ubuntu, the first user by default has a uid of 1000. So if the files were owned by that user, then transferred to another system where the name associated with uid 1000 on that system were different, then it would appear that the permissions were changed.

If you look in /etc/passwd and /etc/group, you can see the uid and gid. Also, if you change the username in that file, log out, then back in, that user's files will all show up as owned by the new username--because the username wasn't stored in the first place.

By the way, uid == user ID and gid == group ID.

---

### Post by Redline21 on 2008-08-28
Ok, that makes sense. Since user1 had a uid of 1000 on the first system, and user2 had a uid of 1000 on the second system, it looked at the number and made him the owner. So as long as I migrate my accounts onto the new system (I was planning to anyhow) I shouldn't have any real issues. Thanks for the help!

---

