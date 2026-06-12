---
title: "I can't save files via SSH"
date: 2008-11-07
forum: General Help
---

### Post by cooldude_832 on 2008-11-07
I have a system in my basement on my network running Ubuntu Server 8.10 

During the install I was prompted to say hey install some thigns so I added:

Apache
MySQL
OpenSSH



I'm now on my desktop upstairs open up putty

I loaded proftpd via
sudo apt-get install proftpd

and when I go to config it via

nano /etc/proftpd.conf

it opens fine but when I go to save it says

error writing /etc/proftpd.conf Premission Denied


Same with any config file for anything.

I log in to SSH via user name I made as my only User account.

Do I need to adjust perms for my user?

---

### Post by Sam on 2008-11-07
No, you need to run sudo to edit these files.
```
sudo nano /etc/proftpd.conf
```

---

