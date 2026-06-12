---
title: "Home Directories"
date: 2008-10-23
forum: General Help
---

### Post by AdamK13886 on 2008-10-23
Hi,

I have recently setup an LTSP server which authenticates against a Windows 2008 server.  The first time a user logs in on the server their home directories are automatically created using the pam_mkhomedir module which points to /etc/skel.  

At the same time this also creates the Videos, Pictures, etc... folders.   How would I disable these folders being created, because each user has their windows home directory mounted upon login, so there is no need for the other folders, plus I am trying to force all users to save their work into the mounted HOME drive.

I have checked in /etc/skel but they are not there.  Is there some script somewhere that I can modify, or will I need to create my own script to delete the folders the first time they logon?

Regards,
Adam

---

### Post by cmnorton on 2008-10-23
Can you configure this server to issue a useradd without creating the directories. Else, you'll have to write a script to go perform an rmdir -p.

If you were creating these directories, then leaving off the -m or other switches to create a home directory would create the account without the home directory.

---

