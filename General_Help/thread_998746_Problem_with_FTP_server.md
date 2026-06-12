---
title: "Problem with FTP server"
date: 2008-12-01
forum: General Help
---

### Post by voodooxombie on 2008-12-01
I set up a FTP server. It is working. I have three users.
1. f1 the home directory for f1 is /home/ftp/docs/f1
2. f2 the home directory for f2 is /home/ftp/docs/f2
3. fm the home directory for fm is /home/ftp/docs

There is a folder called upload in f1 and f2 which is hard linked with the folder upload in the my /home/user1

I want to allow f1 and f2 to write in upload folder and read each others file. :: Till this I managed to get.
But I don't want the file created by f1 to be deleted by f2 and vice versa. :: But the problem lies here.
I set the permission and all but in the uploaded folder f2 is able to delete the file created by f1 and vice versa. 
How could I prevent this? 

Thank you.

---

### Post by cmnorton on 2008-12-06
If I were setting this up, I would rely on native Linux group and user permissions. Basically, if user a1 ftp's files, those files can be uploaded anywhere a1 has the correct user or group permissions. 

What you have set up is a global directory that has to be protected loosely. If you are worried about who logs in and from where, then set up firewall rules to filter certain IP addresses.

---

