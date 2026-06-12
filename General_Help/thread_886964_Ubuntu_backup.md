---
title: "Ubuntu backup"
date: 2008-08-11
forum: General Help
---

### Post by harisund on 2008-08-11
Ok here's the deal. During the regular process of using Ubuntu, I end up breaking various stuff and want to reinstall again. I don't want to go over the process of reinstalling all upgrades and all my customizations (such as to services started, /etc/network/interfaces etc). 

What I am looking for is a way to completely backup my system from a particular point, so that if anything breaks beyond repair I can restore it to the backed-up stage. 

To be cleared, something like Norton Ghost. Something that creates a disk image and restores it. Something like the One-Touch Recovery key on Lenovo laptops. 

Anything Ubuntu specific?

---

### Post by satanik on 2008-08-11
Clonezilla is awesome for this - [http://www.clonezilla.org/](http://www.clonezilla.org/)  <---  would take you 15 mins to do your entire HDD

Also you can tar up your entire hard drive and just untar when booted off the live ubuntu cd.

Hope that helps

---

### Post by der_joachim on 2008-08-12
As a home user, all I ever really needed to back up, were my /etc and /home directories. That should suffice unless you have configured any servers. I once lost my Amarok database, because I had configured it to use mysql. No big deal. 

As for a backup method, I wrote a bash script that mounts an encrypted volume on an external HDD and runs rsync for both my /home and /etc folders. Not only is making a backup vory easy, restoring it is a breeze as well. I do not work with 'restore points' though. If you want incremental backups, I'd suggest taking a look at rdiff-backup. It's in the repos.

---

