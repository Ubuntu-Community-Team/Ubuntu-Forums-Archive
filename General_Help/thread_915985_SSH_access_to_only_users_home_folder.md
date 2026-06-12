---
title: "SSH access to only users home folder"
date: 2008-09-10
forum: General Help
---

### Post by bshosey on 2008-09-10
I would like to set a user to only be able to be in their home directory. I have a user that sftp in to my ubuntu 8.04 server. I only want him to be able to see his home directory I dont even want this user to be able to navigate away from his /home/"USERNAME"/

I also use ssh and do not want to be restricted.

Is this possible?

---

### Post by forger on 2008-09-10
You need sftp or ssh restriction? Your title doesn't match your post :confused:
I think you can restrict them using the **chroot** command

---

### Post by forger on 2008-09-10
1) rssh + chroot: [http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html](http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html)
2) modify your permissions, so that "others" can't see the files/folders.
Usually it's good to restrict the home folder, so that others can't see the other usernames.. as far as system files, I'm not sure.
3) I'm not sure, but you could read about bash -r / restrictive shell
[http://www.gnu.org/software/bash/manual/bashref.html#The-Restricted-Shell](http://www.gnu.org/software/bash/manual/bashref.html#The-Restricted-Shell)
4) Finally, you have chroot jail utilities
in ssh config: [http://undeadly.org/cgi?action=article&sid=20080220110039](http://undeadly.org/cgi?action=article&sid=20080220110039)
package names:
> jailer - Builds and maintains chrooted environments
jailtool - Tool to build chroot-jails for daemons
libapache2-mod-chroot - run Apache in a secure chroot environment
makejail - Automatically create chroot jails for programs
mod-chroot-common - run Apache in a secure chroot environment
rssh - Restricted shell allowing only scp, sftp, cvs, rsync and/or rdist
uml-utilities - User-mode Linux (utility programs)
user-mode-linux - User-mode Linux (kernel)
util-vserver - user-space tools for Linux-VServer virtual private servers

---

### Post by frenchn00b on 2010-06-19
> **forger said:**
> 1) rssh + chroot: [http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html](http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html)
2) modify your permissions, so that "others" can't see the files/folders.
Usually it's good to restrict the home folder, so that others can't see the other usernames.. as far as system files, I'm not sure.
3) I'm not sure, but you could read about bash -r / restrictive shell
[http://www.gnu.org/software/bash/manual/bashref.html#The-Restricted-Shell](http://www.gnu.org/software/bash/manual/bashref.html#The-Restricted-Shell)
4) Finally, you have chroot jail utilities
in ssh config: [http://undeadly.org/cgi?action=article&sid=20080220110039](http://undeadly.org/cgi?action=article&sid=20080220110039)
package names:

and how do you change the /etc/passwd file?

---

