---
title: "vsftpd User Problem"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by al3x2k on 2009-04-19
I have installed and setup vsftpd works great the only issue that i can't upload to directories other then root folder of ftp user.

I have user1 to access machine and i have user2 to access ftp server.
user1 have access to /var/www folder and all subfolders
for user2 i have setup root directory /var/www and shell /bin/false.

The problem is when i login on ftp with user2, i see all contents of /var/www i can upload to it but i cant upload to subfolders :(
How can i change that so user2 can upload to all subfolders of his root directory, thanks.

---

### Post by LoloftheRings on 2009-04-19
seems like you have to change permissions of the /var/www directory. You need to apply permissions recursively.
I don't know the right command for this task, but you could of course simply run ```
gksu nautilus /var
``` and rightclick on www -> properties and change permissions

---

