---
title: "chmod -R 777 ..."
date: 2008-10-04
forum: General Help
---

### Post by Z41n on 2008-10-04
Hello all!

I have accidentally done the command:

```
chmod -R 777 /*
```

Much problems have arised because of this and i want to find a way to restore it.

I have a question, and i would be happy if anybody could answer me. 

Because there is no undo command in linux, i would like to know what other options i have.

Could i run a "restore" program (from a live cd for example), to restore the system files? Because i don't want to loose my serverfiles, i just want to replace the permissions/files that are essential to the system.

My thanks.

---

### Post by porchrat on 2008-10-04
ouch...that is a serious command to run.

What exactly is the system doing now?  Could you define the "problems" you have encountered?

---

### Post by Z41n on 2008-10-04
Indeed.

Well, the problems are like, when running su and entering the password:

```
setgid:operation not permitted
```

Also trying to login using ssh, gives me:
```
Network error: software caused connection abort
```

and sudo problems, in other words, the /bin, /usr/bin, etc all have the wrong permissions. I also don´t know what the normal permissions should be so fixing it is kind of harder. I have webmin running, and using webmin i can change the permissions (lucky me... :) )

---

### Post by oldos2er on 2008-10-04
There is no restore command on the LiveCD that I'm aware of. Back up anything you want to save, then reinstall.

---

### Post by bodhi.zazen on 2008-10-04
You need to either restore from back up or re-install.

---

### Post by porchrat on 2008-10-04
> **Z41n said:**
> Indeed.

Well, the problems are like, when running su and entering the password:

```
setgid:operation not permitted
```

Also trying to login using ssh, gives me:
```
Network error: software caused connection abort
```

and sudo problems, in other words, the /bin, /usr/bin, etc all have the wrong permissions. I also don´t know what the normal permissions should be so fixing it is kind of harder. I have webmin running, and using webmin i can change the permissions (lucky me... :) )

Unfortunately that is an insane task...I mean you could try gong through each directory, subdirectory and file and altering the permissions to restore them to the original state, but that is going to take forever.  You can't merely chmod -R as some of those subdirectories and files will have uniue permissions.  To ask someone to sit with you and check each file is (and I believe I don't merely speak for myself here) a lot to ask.

As has been mentioned already I would recommend backing up what you need in your preferred way and doing a re-install.

Sorry

---

