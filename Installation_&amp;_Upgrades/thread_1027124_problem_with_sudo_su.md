---
title: "problem with sudo su"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by nikhilneela on 2008-12-31
Still the same error persists

when i type chmod 440 /etc/sudoers i get like this.....

nikhil@nikhil-desktop:~$ chmod 440 /etc/sudoers
chmod: changing permissions of `/etc/sudoers': Operation not permitted 
please help me tarus...also when i am logginig in it says that the permissions of file responsible for storing default language has been modified.....what should i do tarus

---

### Post by taurus on 2008-12-31
Boot into recovery mode from GRUB menu and change the permissions of /etc/sudoers back to what it should be.

```
chmod 440 /etc/sudoers
shutdown -r now
```
Next time, stop playing with either ownership or permissions of files outside your $HOME.  If you keep doing that, you would eventually trash your system beyond repair.

---

