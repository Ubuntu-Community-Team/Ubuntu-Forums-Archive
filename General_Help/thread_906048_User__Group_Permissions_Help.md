---
title: "User / Group Permissions Help"
date: 2008-08-31
forum: General Help
---

### Post by cheezewiz on 2008-08-31
Hi Everyone, I think this is my first post on these forums.

I've built a redundant file server using Ubuntu server.  All my backed up files are stored in the directory /files/. I have configured an apache2 virtual host so that [http://myip/files/](http://myip/files/) shows the /files/ directory.  Unfortunately I get a FORBIDDEN error message when I try to navigate to that folder.

I tried making a new user group and adding my user as well as www-data user to it and changing the group ownership of /files/ to my new group and then assigning read, write, and execute permissions for /files/'s group ownership. After doing this I still cannot view the folder in apache nor create or modify files under my user (only the user "files" that owns /files/ can perform any actions).  I am new to linux permissions.  Am I going about this problem all wrong? Thanks.

---

