---
title: "fail to copy and move folder"
date: 2008-10-18
forum: General Help
---

### Post by cloudlor on 2008-10-18
Hi all,

I having problem that moving or copying folder when i was connected with my samba server when using ubuntu desktop. however i try to copy the folder from server to my desktop it show me permission denied. And i try to use the nautilus but it not allow me to connect to server but for local. Anyone have idea with this issue? 

Thank you.

---

### Post by cariboo on 2008-10-18
Do you have ssh set up on your server? IF so you can use sftp to copy or move files nad directories. to use sftp open Nautilus, in the location bar type:

```
sftp://user@server
```

where user@server is you user name and the server name or ip address.

Jim

---

### Post by cloudlor on 2008-10-18
no, i not using any ssh. just a normal samba files server. n i was try in windows vista and windows xp. it working well with my samba. only using Ubuntu desktop it not allow me to do it. is it Ubuntu having some user rights to control the user copy or moving folder?

---

