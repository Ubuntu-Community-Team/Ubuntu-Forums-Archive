---
title: "Xubuntu default usernam/password"
date: 2008-07-16
forum: General Help
---

### Post by brie987 on 2008-07-16
Hi.  I just put dual boot Xubuntu onto my XP desktop, instillation went well but I cannot sign on to Xubuntu with my name and password.  I dont remember putting a name and password is there a default or can I change it or do I have to reinstall it.  I am so frustrated.  Thanks for any help, very much the noob here.

---

### Post by dracayr on 2008-07-16
you entered one at installation ;)

boot in safe mode, then drop to root prompt. execute the command

```
passwd *your username*
```

(if you remember your username.. lol)

EDIT:if you don't remember:
execute 

```
cat /etc/passwd | cut -d: -f1
```all users will be listed


dracayr

---

### Post by brie987 on 2008-07-17
Thanks for your reply, Im so new to Xubuntu I don't even know how to boot into safe mode in Xubuntu, XP I know.  I just reinstalled and paid extra attention this time.  I put a new user and password.  Again thanks.

---

### Post by aysiu on 2008-07-17
> **brie987 said:**
> Thanks for your reply, Im so new to Xubuntu I don't even know how to boot into safe mode in Xubuntu, XP I know.  I just reinstalled and paid extra attention this time.  I put a new user and password.  Again thanks.
This should help you, in case you ever need to boot into recovery mode in the future:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by brie987 on 2008-07-20
Thanks.  This is really handy.

---

