---
title: "how to connect to samba with another user identity?"
date: 2008-07-11
forum: General Help
---

### Post by David Shen on 2008-07-11
Hi,

from the samba log, i see that i am always connecting to my samba server with my window hostname. how to change that identity? i want to provide that identity directly to the URL.

thanks.

---

### Post by justleen on 2008-07-11
you can add samba user with ```
 smbpasswd user password
```

after that, edit the /etc/samba/smb.conf file (the shares are at the end of file) if will have a section for allowed users there. Add the users you have set a passwd for.

---

### Post by David Shen on 2008-07-13
Thanks.

So, should the user name be the same as my windows user account, or whatever is ok?

---

