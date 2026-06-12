---
title: "Samba server: force group option doesn't work"
date: 2008-08-28
forum: General Help
---

### Post by cyrus_the_virus on 2008-08-28
Hi,

I'm trying to set up a samba share for a special download account on my server. All files that are uploaded to this share should be owned by the download group so that the download user (also in the download group) can open them.

However when I use the force group option in smb.conf the share is not accessible. When trying to access it from windows I get this error: "the specified group does not exist". When I remove force group the share is accessible but then the group for uploaded files is wrong.

Any ideas why this is? The users that can access the share are all member of the 'download' group (it's not their primary group though)

This a part of my smb.conf:

> 
[global]
    workgroup = WORKGROUP
    server string = %h server (Samba, Ubuntu)
    log file = /var/log/samba/log.%m
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    encrypt passwords = true
    obey pam restrictions = yes
    invalid users = root
    unix password sync = yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    pam password change = yes
    map to guest = bad user

[downloaded_files]
    comment = Download
    path = /media/hdb/download/
    valid users = user1 user2 user3
    browseable = Yes
    available = Yes
    read only = No
    inherit acls = No
    create mask = 0750
    force create mode = 0750
    directory mask = 0750
    force directory mode = 0750
   **force group = download**


Marty

---

