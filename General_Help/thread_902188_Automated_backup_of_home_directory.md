---
title: "Automated backup of home directory"
date: 2008-08-27
forum: General Help
---

### Post by gpb on 2008-08-27
I would like to automate a backup of my home directory once a day through the CLI Can anybody help with the command to use to automate the backup????

---

### Post by justleen on 2008-08-27
you can simply place something like this in your crontab 
```

crontab -e  ## edit crontab
1 0 * * * tar -cvf /media/backup/`date +%Y%m%d`homedir.tar.gz /home/username

```

that will backup your home dir @00.01 everynight, and name it 20080827homedir.tar.gz

---

### Post by sameerds on 2008-08-27
> **gpb said:**
> I would like to automate a backup of my home directory once a day through the CLI Can anybody help with the command to use to automate the backup????

```
sudo aptitude install rsnapshot
```

That's the simplest tool around.

---

### Post by sameerds on 2008-08-27
> **justleen said:**
> you can simply place something like this in your crontab 
```

crontab -e  ## edit crontab
1 0 * * * tar -cvf /media/backup/`date +%Y%m%d`homedir.tar.gz /home/username

```

that will backup your home dir @00.01 everynight, and name it 20080827homedir.tar.gz

That makes sense only in the case of tape drives and such. If the intention is to just keep a copy on another disk, this is overkill. The number of files that change in a day are usually much smaller than the total files in your home. Making one tarball every day is a waste of space as well as processing power. It's better to use differential backups using rsync along with hardlinking.

rsnapshot is a tool meant to do just that. It makes a copy of your home every day, but does not use space for files that have not changed, by hardlinking them. It also rotates backups, so that you don't have an indefinite list of backups. Instead you can configure it to keep backups for a given number of days and then delete the older ones.

---

### Post by rbmorse on 2008-08-27
I use sbackup for that. Works, has a nice little setup GUI, it's in repository and so easy to set up even a caveman could do it.

---

### Post by DGortze380 on 2008-08-27
the command would be:

```

sudo rsync -axz /home /media/**my_backup_disk**

```

replace anything in **  **  with the appropriate path.

This will backup anything in /home to the destination you input. The first time it will create a complete backup, second time it will add any new files update and changed files. If you want it to delete any files that have been deleted then use this one.

```

sudo rsync -axz --delete /home /media/**my_backup_disk**

```

Load either into cron as stated above to run daily. Be careful with the delete flag when loading into cron, you will only essentially have 1 day to restore your backups if you use it.

---

