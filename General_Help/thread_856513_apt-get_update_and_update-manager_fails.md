---
title: "apt-get update and update-manager fails"
date: 2008-07-11
forum: General Help
---

### Post by robaldred on 2008-07-11
Hi,
I cannot do anything with the update manage or apt
I receipt the following error:

> 
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing lilypond (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


Any ideas?
Rob

---

### Post by DagMan on 2008-07-11
I had a similar problem to this a long time ago but I don't remember now if it is the same thing.  It won't hurt to try though, to back up your sources.list file, update, then restore the file and update again.  If it doesn't work then no harm done I don't think
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
sudo echo " " >  /etc/apt/sources.list
sudo apt-get update
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
sudo apt-get update
```

---

