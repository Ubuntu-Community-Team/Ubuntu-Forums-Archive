---
title: "Monitor folders for changes"
date: 2008-08-28
forum: General Help
---

### Post by mastermindg on 2008-08-28
I am looking to create a script that will actively monitor a folder and create another script that will backup any changes made to another folder on   an external drive.

Anybody have any ideas?


**P.S.**
[B][SIZE="4"]
Don't suggest cp[/SIZE][/B]:

I was originally thinking of just using cp -u -r, however files are deleted as well as created, so I will have to take this into account as well.

---

### Post by arch0njw on 2008-08-28
How often do you need it to do this?  I just got "simple backup" working and it is awesome.  I have it doing a monthly full backup and a weekly incremental.  You can specify which folder/s to watch and what to exclude.

sbackup is the package name is you prefer CLI installations.

---

### Post by mastermindg on 2008-08-28
Doesn't 'simple backup' compress to tar?

I'm not looking to backup my drive, per se, this is strictly to ***mirror*** the folder to another folder, which happens to be on an external drive.

---

### Post by arch0njw on 2008-08-28
rats.  right, it does.

What about setting up a script with rsync?  You could put that on a cronjob too.  rsync is meant for mirroring.

---

### Post by mastermindg on 2008-08-28
Yes!

After researching a little more, I've realized that rsync will be my best bet for this.

This idea came about because I went to use Komparator, but it took forever to index the files and then it has hardly any command-line options.

Rsync will work well for me as I have thousands of files to sync. I have to do some more research to determine if I can set it up to sync once a day rather than constantly spinning my drives.

Thanks for the nudge arch0!

:guitar:

---

### Post by DGortze380 on 2008-08-28
> **mastermindg said:**
> Yes!
I have to do some more research to determine if I can set it up to sync once a day rather than constantly spinning my drives.
:guitar:

use cron to run it daily.

```

man crontab

```

may be a good idea to add it to root's cron unless the folder is in your home directory.

---

### Post by arch0njw on 2008-08-28
> **mastermindg said:**
> Rsync will work well for me as I have thousands of files to sync. I have to do some more research to determine if I can set it up to sync once a day rather than constantly spinning my drives.


As mentioned, crontab is your friend.  I recommend making a small shell script that calls rsync.  That way you can (1) call it from a cron job, and (2) call it on-demand.  I just remembered I have a script that does this.


```

#!/bin/sh

rsync -avz -e ssh /home/me/dir-to-sync me@machine:/home/me/target-dir

exit

```You could do this to mounted media like this:

```

#!/bin/sh

rsync -avz /home/me/dir-to-sync /media/mounted-drive/target-dir

exit

```But don't take me literally there.  Please read up on rsync (man rsync).

---

### Post by mastermindg on 2008-08-28
This is what I'll use:


```
#!/bin/sh

rsync -vrtz --delete /home/me/dir-to-sync /media/mounted-drive/target-dir >> /home/me/rsync.log

exit
```

The two folders in question are running on FAT32 because of the need to transfer files to/from windows systems. Unfortunately there are still people who use Windows :)
 
So archive won't do me any good since permissions are not really an issue here. Times are important because I only want to transfer newer files, compression is also important because of the number of files, Delete is also critical because I will delete files from time to time on the source. 

Another question:

My external drive is a WD MyBook and due to the nature of the drive, it goes into hibernation after inactivity. I would need to put a couple of lines in my script to check if the drive is mounted, and if not.. to mount it. Any ideas?

---

### Post by arch0njw on 2008-08-28
> **mastermindg said:**
> My external drive is a WD MyBook and due to the nature of the drive, it goes into hibernation after inactivity. I would need to put a couple of lines in my script to check if the drive is mounted, and if not.. to mount it. Any ideas?

Oh sweet merciful $_deity, I have a My Book too and that drives me BONKERS!

I haven't delved into this too deeply because I found a couple of tolerable ways around it (for me).  These are *really* lazy ways, so take with salt, sugar, honey, LSD, and who knows what else:

1. I will have a terminal open and CD to that drive.  Just by doing that, it doesn't sleep.  It will spin down, but not completely sleep.
2. If I am going to use it to run VMs (which is what I normally do), then I do so immediately.  As long as a VM is running, it stays awake.

I use the eSATA connection on mine, so not sure if this will be applicable to USB.  _However_, I also have a FreeAgent which I read bad things about.  (I didn't have a choice about getting it -- I was "issued" it).  I did some really sloppy searching and haven't delved into it.  The FreeAgent drives apparently have the same problem, and some folks have found a way around it.  Here are my bookmarks on this issue:

[http://www.google.com/search?q=ubuntu+seagate+freeagent](http://www.google.com/search?q=ubuntu+seagate+freeagent)
[http://alienghic.livejournal.com/382903.html](http://alienghic.livejournal.com/382903.html)
[http://ubuntuforums.org/showthread.php?t=494673](http://ubuntuforums.org/showthread.php?t=494673)
[http://forums.majorgeeks.com/showthread.php?t=133348](http://forums.majorgeeks.com/showthread.php?t=133348)

HTH, and if it does, please let me know because I haven't tried this yet.  :)

---

### Post by mastermindg on 2008-08-28
OK, I'm good with cd'ing into the directory. :)

I'll check out other options, but this is ok for now.

Thanks again.

---

