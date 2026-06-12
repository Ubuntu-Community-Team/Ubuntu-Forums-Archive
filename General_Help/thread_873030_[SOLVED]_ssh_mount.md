---
title: "[SOLVED] ssh mount"
date: 2008-07-28
forum: General Help
---

### Post by bonfire89 on 2008-07-28
I have mounted ssh before, I really don't know why these commands wouldn't work, seems to make sense.. hmm

if someone could please give these a look it would be a big help

```

tory@tory-laptop:~$ ssh myUserName@ssh.netfirms.com
myUserName@ssh.netfirms.com's password: 
myUserName % pwd
/mnt/b02e/www
myUserName % 
myUserName % logout
Connection to ssh.netfirms.com closed.
tory@tory-laptop:~$ mkdir sshmyUserName
tory@tory-laptop:~$ sudo chown tory sshmyUserName
[sudo] password for tory: 
tory@tory-laptop:~$ sudo sshfs myUserName@ssh.netfirms.com:/mnt/b02e/www ~/sshmyUserName
myUserName@ssh.netfirms.com's password: 
tory@tory-laptop:~$ cd sshmyUserName
bash: cd: sshmyUserName: Permission denied
tory@tory-laptop:~$ 

```

---

### Post by ktrnka on 2008-07-28
```
sshfs username@host:/path/to/share /local/mount/point -o allow_other
```

The -o option allows access to other users

---

### Post by bonfire89 on 2008-07-28
there, we go, that edit worked! 

Thank you!

---

### Post by ktrnka on 2008-07-28
Sorry, forgot one more thing. You need to edit /etc/fuse.conf and uncomment user_allow_other. Then do the sshfs mount with the -o allow_other option.

---

### Post by ktrnka on 2008-07-28
> **bonfire89 said:**
> there, we go, that edit worked! 

Thank you!

Oh ok, guess you did that already! haha

---

