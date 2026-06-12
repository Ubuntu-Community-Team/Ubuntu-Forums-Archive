---
title: "Mounting a shared drive for user with virtualbox"
date: 2008-10-11
forum: General Help
---

### Post by daicoden on 2008-10-11
Hi,  I am trying to mount a shared drive using the following command...
```

sudo mount -t vboxsf min windows/ -o uid=1000,gid=1000

```

min is the name of the share

I then run ls -l windows ...
drwxrwxrwx 1 daicoden daicoden        0 2008-09-10 11:16 Class Work
...

so it says that I have permission, but if I try to create a directory as my user in the folder windows i get permission denied.  I can create a folder as root though...

However if I make a folder in Class Work as my user I am able too.

Am I missing something that is causing problems with that root folder?

Also is there anything wrong with this?  After the permissions I would like to use fstab... It isn't working...
```

min    /home/daicoden/windows    vboxsf    uid=1000,gid=1000   0    0

```

---

