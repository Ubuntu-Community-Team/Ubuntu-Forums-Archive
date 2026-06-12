---
title: "filesystem trouble"
date: 2008-09-29
forum: General Help
---

### Post by JoSSte on 2008-09-29
I have a system with three harddrives all P-ATA. 

/dev/sda3 is mounted as / 
/dev/sdc1 is mounted as /home/mylogin/diverse
/dev/sdb1 is mounted as /home/mylogin/backups

all formatted as ext3

***1.***

The machine in question runs nagios, and as a part of that setup it has a set of ssh-keys generated with ssh-keygen and copied to the remote machines with ssh-copy-id.

Recently there was a patch to nagios which for some reason removed my nagios user's ~/.sshand formatted as ext3/ contents, so i had to start over. I though that I'd chattr. the id_rsa files to prevent the installers and updaters from altering them. But I get the following error even if i use lsattr:

```
nagios@socrates:~/.ssh$ lsattr
lsattr: Inappropriate ioctl for device While reading flags on ./id_rsa.pub
lsattr: Inappropriate ioctl for device While reading flags on ./id_rsa
```

```
nagios@socrates:~/.ssh$ chattr +i id_rsa
chattr: Inappropriate ioctl for device while reading flags on id_rsa
```

- all the posts I have found with this error seem to be people running the command on reiserfs. but I *am*


***2.***
i also noticed that some files on the /home/mylogin/backups suddenly have a size of 0 bytes, but I haven't done anything to them. 

- are all these errors symptoms of soon-to-crash hard drives - or something else?

*Please*! If you have *any* comments *please* post them!

---

### Post by DaJL on 2008-10-20
did you manage to fix this?  I got the same issue on my laptop.  I did a tar of the whole system  and applied the image on a new workstation  and I still get that same error. And yes its ext3

---

