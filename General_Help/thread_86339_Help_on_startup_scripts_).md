---
title: "Help on startup scripts :)"
date: 2005-11-04
forum: General Help
---

### Post by secondred on 2005-11-04
I searched the forum for the procedure and i know it's in the init.d folder. And i've gotten it to work. Yay.

My problem is the script is executed by root. Is there a way to make the script i put in init.d executed by a super user? Attaching screen from ssh would be easier. I don't have to run the su command everytime.

Thanks in advance for the replies.

---

### Post by adwait on 2005-11-04
Root can execute any command as any user, simply put
```
su <username> <command>
```

I don't know what you mean when you say that you want to run su every time.......If you use this, it won't ask you for the password since you are doing this as root,

---

### Post by secondred on 2005-11-04
thanks for the reply.

---

