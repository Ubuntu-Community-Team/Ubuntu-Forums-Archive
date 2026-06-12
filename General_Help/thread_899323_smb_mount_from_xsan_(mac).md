---
title: "smb mount from xsan (mac)"
date: 2008-08-24
forum: General Help
---

### Post by Hunz on 2008-08-24
hi,

i am trying to mount an xsan (apple storage), i used this command:

mount -t smbfs -o username=user,password=password,rw,uid=0,gid=0,fma sk=777,dmask=777 //ip/folder/ /mnt/san/

and i always get this error message

5203: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

i can ping from both machines, and the wierd thing is i can access the san using the GUI and i got read write permissions and i also accessed these files from a windows machine but with only read permissions, amd when i try to mount the san on /mnt/san it always gives the same error.
anybody has any ideas how to solve this problem???

thanks in advance

---

