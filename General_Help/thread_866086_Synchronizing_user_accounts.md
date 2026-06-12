---
title: "Synchronizing user accounts"
date: 2008-07-21
forum: General Help
---

### Post by creativepragmatic on 2008-07-21
Hello everyone,

I have Ubuntu installed on 2 machines.  The machines are used by the same users.  I would like to synchronize user accounts between the 2 machines so that the accounts mirror each other.

Does anybody know of a package utility that can do this?

Thank you in advance for any ideas,

Orville

---

### Post by dracayr on 2008-07-21
you should be able to copy all the data from /home/user1 on the 1. machine to /home/user2 on the 2. machine. If you do this with a file manager rather than via command line, make sure you also copy the configuration files, which are by default hidden in most file managers. to see them in nautilus, press Ctrl+H.

dracayr

---

### Post by CatKiller on 2008-07-21
If one of the machines is always on, you could mount the home folders from that machine as the home folders on the second machine using NFS.

---

### Post by creativepragmatic on 2008-07-21
Hi dracayr,

Thank you for responding.  Simply moving files across the network is a manual solution.  What I would like to do is set the two machines up so that they automatically mirror each other across the network without any user intervention.  That way each user can use a machine and have any file updates reflected on the other machine and vice versa.

Orville

---

### Post by creativepragmatic on 2008-07-21
CatKiller,

That's an idea that I never thought of and I have taken note of it for future reference.  In this case, only one machine is likely to be on at a time.

Thank you for responding.

Orville

---

### Post by bodhi.zazen on 2008-07-21
Would something like rsync work ?

---

### Post by tamoneya on 2008-07-21
you probably want to look into rsync.  It will manage any differences between the two computers without much bandwidth since it just sends the difference everytime not the entire files.  If you set up some cron job to run an rsync command hourly it should work pretty well.  Then as long as the computers are sometimes on at the same time they will keep themselves in sync with each other.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by creativepragmatic on 2008-07-21
bodhi.zazen and tamoneya,

Thank you for responding.  I had been thinking of using 'rsync' since it is the only method I know of automatic backup on Linux.  I had really put this post up hoping for a neater solution.

Would rsync have to be installed on both computers?

Thanks for the link tamoneya.

Thanks again,

Orville

---

### Post by bodhi.zazen on 2008-07-21
These links may help :

[http://lists.samba.org/archive/rsync/2002-October/003823.html](http://lists.samba.org/archive/rsync/2002-October/003823.html)

[http://allyourtech.com/content/articles/14_11_2005_synchronizing_files_with_rsync.php](http://allyourtech.com/content/articles/14_11_2005_synchronizing_files_with_rsync.php)

Personally, I advise you set one as master.

The alternate is to set a shared data directory and share it via a network protocol. sshfs, samba, or nfs (in order of security).

---

### Post by creativepragmatic on 2008-07-21
bodhi.zazen,

Thank you again for the links and advice.  I think I have everything I need to get this going later on in the week.  

Thank you all again.

Orville

---

### Post by MemoryDump on 2008-07-21
I'd recommend using [NIS]("https://help.ubuntu.com/community/SettingUpNISHowTo") for username/password syncing and [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") for your /home files.

-MD

---

