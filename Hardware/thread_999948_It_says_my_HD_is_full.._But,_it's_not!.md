---
title: "It says my HD is full.. But, it's not!"
date: 2008-12-02
forum: Hardware
---

### Post by DroBuddy on 2008-12-02
Hello everyone,


I'm running Ubuntu 8.10 with the latests updates and for some reason it says that my HD is full (only 320 MB free) on a 60 GB partition... Granted, I have a lil' over 11 Gigs in files, plus a few software packages on top of the OS, but that's not what's taking up all of my space. I deleted about 20 Gigs in files and it still says I have approx. 300 Mb avail?!

I had 'Simple Backup' setup to auto-create incremental backups which took up about 15 Gigs and I had my torrents (which are set to preallocate) and that was about another 5 Gigs. I deleted all of these files, rebooted and it still says there's only 300 Mbs available! 

So, I can't even retrieve my e-mail with Evo right now because I supposedly don't have enough disk space available. ::sighs::

I'm stumped... I'd greatly appreciate any help / insight anyone may have to share. ;)


Peace.

---

### Post by taurus on 2008-12-02
When you delete files, make sure you empty your trash bin or else those files still reside on your harddrive, taking up space that you thought you have recovered.

Post the output of this command from a terminal.

```
df -h
```

---

### Post by DroBuddy on 2008-12-03
[HTML]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              60G   57G  308M 100% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  212K  504M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  556K  504M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-9-generic/volatile[/HTML]


So, how would I perma delete things that are in my trash? There's one folder shown in there that wont delete due to permissions; but I can't restore it 'cause the merge will mess up my current files in the directory, and I don't have enough available space to move the files elsewhere prior to restoring the folder..?

I tried using nautilus, but that didn't work...

And, to top it off, the folder is only a few hundred Mbs... So, where's those other 20 gigs gone? They were too big to be moved to trash, so they should have been deleted on the spot. Wouldn't that have opened up free space? Or, would they be stuck in the trash and just not showing? ::shrugs::

---

### Post by Nathan Sweeney on 2008-12-03
> **DroBuddy said:**
> [HTML]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              60G   57G  308M 100% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  212K  504M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  556K  504M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-9-generic/volatile[/HTML]


So, how would I perma delete things that are in my trash? There's one folder shown in there that wont delete due to permissions; but I can't restore it 'cause the merge will mess up my current files in the directory, and I don't have enough available space to move the files elsewhere prior to restoring the folder..?

I tried using nautilus, but that didn't work...

And, to top it off, the folder is only a few hundred Mbs... So, where's those other 20 gigs gone? They were too big to be moved to trash, so they should have been deleted on the spot. Wouldn't that have opened up free space? Or, would they be stuck in the trash and just not showing? ::shrugs::

Maybe you could try using the find command to find files greater than say 500MB?  I think you could do:

```
sudo find / -f -size +500000k
```

---

### Post by DroBuddy on 2008-12-03
Terminal returns:

> find: unknown predicate `-f'

Any other ideas?  ;)

---

### Post by Onesimus on 2008-12-03
I was unclear from your last reply whether you had emptied your 'Deleted Items' folder.  To do this start up Nautilus, and select File->Empty Deleted Items.

If you have already done this, then not sure what the problem might be.

---

### Post by tommcd on 2008-12-03
Run this in terminal:
```
sudo du -csh /*
```
This may take a minute to run. It will show the size of each directory on / (root). It will also show a grand total at the end. 
If you find one directory that is unusually large, you can focus on that directory like this:
For example, suppose /tmp or /var are very large. Then use the "du" command like this to focus on those directories:
```
sudo du -csh /tmp/*
```
```
sudo du -csh /var/*
```
Then, suppose /var/log is huge. To focus on that, run:
```
sudo du -csh /var/log/*
```
In this way you can find out what is taking up all your hard drive space to see what you can delete to free up space.

---

### Post by starfry on 2008-12-03
You may be out of inodes. This can happen if you have loads of files.

Use "df -ki" to show inode count.

It's easy to run out of inodes if you have a large number of small files. The bad news is you have to remake the file system to increase the number of available inodes.

---

### Post by hysteresis on 2008-12-03
If you deleted large files somehow as "root", your trash is in the root folder and does not show up on your trash icon. If you <alt-F2> gksu nautilus and look in your root trash (/root/.local/share/trash/files), there may be some large files to delete. if there are files, send /root/.local/share/trash to trash. You will then be prompted to delete the folder. If you try to send the files individually to trash, they will reappear instantly. Note: /root/.local is a hidden file.

---

### Post by DroBuddy on 2008-12-03
And he winner is... Hysteresis! When I ran the "sudo du -csh /*" cmd that tommcd suggested, it showed that there was over 40 gigs in the root directory. After following Hysteresis' directions, I navigated to the Trash folder to find (pretty much) all of it sitting there. So, after moving the files to trash in Nautilus and deleting them (again), we're good to go!

Thanks again everyone for your time and advice. I greatly appreciate it. ;)


Peace.

---

### Post by glotz on 2008-12-03
[QUOTE=starfry]You may be out of inodes. [...] The bad news is you have to remake the file system to increase the number of available inodes.[/QUOTE]I was wondering if archiving some files would free some inodes? Just curious.

---

