---
title: "xp lan access denied to U 8.04 shared files"
date: 2008-11-25
forum: General Help
---

### Post by hubiedo on 2008-11-25
i have my xp laptop and desktop ubuntu 8.04 set up on the same workgroup name. from linux system can access all shared files on the win2k desktop and winxp laptop on the lan with no problem.

 win xp can see and shows the samba server? on linux desktop. when i click on it it sz you may not have access privleges etc. access denied.

can anyone help? any suggestions would be appreciated. 

once i did get into see the shared files but got the same "access denied". i have marked the shared files as ok for all users. when i did get to the shared files on the linux sys it asked for a user name and password and wouldn't take the user names assigned on the linux box. and again gave "access denied" 

i know samba is working but i don't know what i did wrong here.

i know you guys probably get this all the time but i don't how to solve it.

---

### Post by cariboo on 2008-11-25
It sounds like you have a permissions issue. Have you gone into the directory in a terminal and set the perrmissions manually like this:

```
sudo -R 777 /shared_files
```

Where shared_files is the directory that you have set up as a share.

Jim

---

