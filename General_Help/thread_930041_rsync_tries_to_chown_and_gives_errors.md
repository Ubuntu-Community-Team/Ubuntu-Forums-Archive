---
title: "rsync tries to chown and gives errors"
date: 2008-09-25
forum: General Help
---

### Post by skelooth on 2008-09-25
I get the following errors

rsync: chown "/mnt/backups/patrick/etc/power/scripts.d" failed: Permission denied (13)


on almost all files when I run the commands:
```

mount //nas5200/Backups /mnt/backups -t smbfs -o user,credentials=/home/pavella/Desktop/cred_file,iocharset=utf8,file_mode=0777,dir_mode=0777
rsync -av --delete --exclude '/proc' --exclude '/sys' --exclude '/tmp' / /mnt/backups/patrick
```

Any ideas? nas5200 is a thecus NAS with NFS shares enabled.

---

### Post by skelooth on 2008-09-26
bump, anyone? Any thing I've found on google has been posts and email threads with no replies.

---

### Post by russlar on 2008-09-26
Part of the problem is that you're not excluding /mnt/backups on your rsync, effectively rsyncing your backup to itself.

Don't know if that'll fix the chown issue, but that is the location of the file you cited.

---

### Post by skelooth on 2008-09-26
Wow, I guess that was a small over(under) sight. Thank you for catching that, I would have ended up rsyncing the entire network.

Unfortunately I still get those permission errors on chown, I also get a permission denied error trying to copy the .gvfs folder despite temporarily setting it to 777. I don't get any of these errors when I rsync on my local system to a local folder.

When it crawls over the previously moved files it spits out massive amounts of permission errors
```

rsync: chown "/mnt/backups/patrick/usr/lib/ppr" failed: Permission denied (13)
usr/lib/ppr/interfaces/
rsync: chown "/mnt/backups/patrick/usr/lib/ppr/interfaces" failed: Permission denied (13)
rsync: symlink "/mnt/backups/patrick/usr/lib/ppr/interfaces/foomatic-rip" -> "../../../bin/foomatic-rip" failed: Permission denied (13)
rsync: symlink "/mnt/backups/patrick/usr/lib/ppr/interfaces/ppromatic" -> "foomatic-rip" failed: Permission denied (13)
usr/lib/ppr/lib/
rsync: chown "/mnt/backups/patrick/usr/lib/ppr/lib" failed: Permission denied (13)
rsync: symlink "/mnt/backups/patrick/usr/lib/ppr/lib/foomatic-rip" -> "../../../bin/foomatic-rip" failed: Permission denied (13)
rsync: symlink "/mnt/backups/patrick/usr/lib/ppr/lib/ppromatic" -> "foomatic-rip" failed: Permission denied (13)
usr/lib/psutils/
rsync: chown "/mnt/backups/patrick/usr/lib/psutils" failed: Permission denied (13)
rsync: chown "/mnt/backups/patrick/usr/lib/psutils/md68_0.ps" failed: Permission denied (13)
rsync: chown "/mnt/backups/patrick/usr/lib/psutils/md71_0.ps" failed: Permission denied (13)
usr/lib/pulse-0.9/

```

If I ever tried to restore my system with a reverse rsync, would this effect me? (wouldn't everything default to root owner anyway, then I can just fix the www-data user?)

---

### Post by Titan8990 on 2008-09-26
I don't know why it is trying to chown but from my experience I have always had to run rsync as root. My cron for rsync is part of root's crontabs.

> If I ever tried to restore my system with a reverse rsync, would this effect me? (wouldn't everything default to root owner anyway, then I can just fix the www-data user?)


Always sudo it....

---

### Post by skelooth on 2008-09-26
I am:\ that's why I'm confused. I understand why it chowns (to maintain proper permissions if you need to restore), but I don't understand why my sudo/root is having so many permission problems. 

I run my script with sudo bash myscript.sh, but even if I do sudo bash then call it, I still get the errors. Do you think the copies it's making are integral?

---

### Post by Titan8990 on 2008-09-26
Just noticed. Your backup drive is a SMB share??

---

### Post by skelooth on 2008-09-26
Yeah, it's an NAS that serves files with NFS. Should I not be mounting with samba?

---

### Post by Titan8990 on 2008-09-26
If it is not formatted in EXT3 you will not be able to use EXT3 permissions on it. I was having issues with restoring a backup that I was making via rsync to a NTFS formatted drive and the permissions were not being preserved (due to how permissions work differently in NTFS).

---

### Post by skelooth on 2008-09-26
Interesting and really obvious, I should have thought of that as well. I'll just tell it --no-owner --no-group then, I've already stripped it down to only sync a handful of directories (bin, etc, usr, var, home). Being able to restore the full OS is not a big deal, I just don't want to lose any work. 

Thank you for the help.

---

### Post by Titan8990 on 2008-09-26
Glad to help.

You should note that any files restored from it (going off of memory) will all be owned by root with 644 permissions.

---

### Post by skelooth on 2008-09-26
Yeah, this is what I'm learning. Even with the cavaets I think this is a faster and stronger solution than some of my other options. It's just not economical to copy and shuffle images of disks or full archives of installations around.

even with --safe-link I'm getting errors on all of the symbolic links

I'm also getting things like this
```
rsync: recv_generator: mkdir "/mnt/backups/patrick/var/cache/system-tools-backends/backup/9" failed: Permission denied (13)
*** Skipping everything below this failed directory ***

```

But I think I'm going to turn a blind eye or maybe just specifically exclude them.

---

