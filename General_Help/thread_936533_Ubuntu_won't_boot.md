---
title: "Ubuntu won't boot"
date: 2008-10-02
forum: General Help
---

### Post by quengilar on 2008-10-02
I can't get Ubuntu to boot, it opens up and gets to the loading screen but then it says 
/dev/shm/root contains a file system with errors, check forced
it does the check and then says
/dev/shm/root : UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
            (i.e., without -a or -p options)
fsck died with exit status 4
then down a bit it says
The program 'apt-get' is currently not installed. You can install it by typing: apt-get install apt
so i do that and it repeats that. If you could tell me the command for booting a live cd from root@ubuntu:~# I could wipe the hard drive and reinstall Linux or does someone have a better idea? :confused:

---

### Post by WWSmith36 on 2008-10-02
> The program 'apt-get' is currently not installed. You can install it by typing: apt-get install apt

If apt-get is not installed - how the heck can you get it with an apt-get command.

---

### Post by WWSmith36 on 2008-10-02
Seriously

If this a brand new install.  With this being the first boot.  If it is I think you should boot the LiveCD that you used to install and select, check CD for defects.

---

### Post by Bungo Pony on 2008-10-02
If this is a fresh install, you may want to try a reinstall.

If this is an existing install, it's possible that your hard drive may be dying.


I had this problem not long ago, and fsck fixed it.

---

### Post by quengilar on 2008-10-03
the install is an update and something got messed up I guess, I would try to reinstall but the cd drive doesn't register with the computer and that makes it impossible to boot off of unless i figure out a way to do it

---

