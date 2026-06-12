---
title: "backuppc and root?"
date: 2008-08-05
forum: General Help
---

### Post by nycjeff on 2008-08-05
Hi,
I'm trying to install backuppc on an old machine to use as a backupper for my main machines. 
I'm having difficulty and part of my confusion comes with the usage of a root user.
In the community documentation [here]("https://help.ubuntu.com/community/BackupPC")
you don't seem to need to do anything with root if you're using rsync. 
yes if you're using the tar method, but not if you're using rsync.
But that doesn't seem to jive with most of what I'm reading in the backuppc documentation. 
I'm probably thinking about this incorrectly, and was hoping someone could help straighten me out.

---

### Post by Scunge on 2008-08-24
It would appear that the presence of "root" in the rsync commands must do it somehow.

However, the setup there for rsync is not how I set mine up. which I got pretty much completely from [**[color=blue]this guide[/color]**](http://maia.deec.uc.pt/Computers/Operating_Systems/Linux/Servers/Backups/Backuppc/Getting_started):

As you can see, this does a sudo on a file which issues the rsync command, and so there is a line in the sudoers file like the one for tar in the [**[color=blue]community documentation[/color]**](https://help.ubuntu.com/community/BackupPC). Perhaps something like that is what's required in that page as well:
```
backuppc ALL=NOPASSWD: /usr/bin/rsync
```
I don't know.

One point of note: when I installed BackupPC, I hit the bug that sendmail wasn't included in the dependencies in Dapper and Feisty's versions of BackupPC, so make sure that you install sendmail first. See [**[color=blue]this  bug report[/color]**](https://bugs.launchpad.net/ubuntu/+source/backuppc/+bug/90362).
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

