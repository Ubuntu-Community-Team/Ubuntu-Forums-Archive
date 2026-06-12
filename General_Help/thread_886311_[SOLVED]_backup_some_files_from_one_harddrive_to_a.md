---
title: "[SOLVED] backup some files from one harddrive to another"
date: 2008-08-11
forum: General Help
---

### Post by whorush on 2008-08-11
hi, i have a big hard drive, and a small one.  i want to use the small one just to back up the big one, should it die.

of course, i just want to back up some important directories of the big one.

i figure it should happen every night, and stuff that has changed should be moved over and overwritten.  that kind of thing.

i've looked at a lot of backup utils, but nothing seems to do the job.

any advice?

thanks!
bradley

---

### Post by ramnarayan on 2008-08-11
> **whorush said:**
> 
i've looked at a lot of backup utils, but nothing seems to do the job.

any advice?

Try rsync

the CLI command is sudo rsync -avz /source/sourcex  /destination

If you have multiple directories then you have to run this multipletimes with the source x being the different sources 

onceyou run it successfully just copy the the command to a text file and next time just run it , or you can make a short cut launcher for each destination.

There is a way of making a script but maybe some script write can tell you how ?

And i guess ifyou use one of the time management software you could easily time it for a daily run.

But please not that this rsync command make an incremental back up.

And it is very efficient and easy one. 

Also read the man pages

ram

---

### Post by hyper_ch on 2008-08-11
> **ramnarayan said:**
> If you have multiple directories then you have to run this multipletimes with the source x being the different sources 

or make use of the include parameter.

---

### Post by whorush on 2008-08-13
wow!  thanks guys, that was one of the easiest things i've ever done on linux!  SOLVED.

---

### Post by whorush on 2008-08-13
wow!  thanks guys, that was one of the easiest things i've ever done on linux!  SOLVED.

```
rsync -avz   /home/brad/Desktop/              /media/disk/Desktop   --exclude "docs/"
rsync -avz   /home/brad/Desktop/docs/backup   /media/disk/backup
rsync -avz   /home/brad/.mozilla              /media/disk/.mozilla
rsync -avz   /home/brad/.VirtualBox           /media/disk/.VirtualBox
```

---

### Post by DGortze380 on 2008-08-13
> **whorush said:**
> wow!  thanks guys, that was one of the easiest things i've ever done on linux!  SOLVED.

```
rsync -avz   /home/brad/Desktop/              /media/disk/Desktop   --exclude "docs/"
rsync -avz   /home/brad/Desktop/docs/backup   /media/disk/backup
rsync -avz   /home/brad/.mozilla              /media/disk/.mozilla
rsync -avz   /home/brad/.VirtualBox           /media/disk/.VirtualBox
```

You can easily put those in a script and load the script into cron to run automatically in the background whenever you want.

---

### Post by hyper_ch on 2008-08-14
shouldn't the exclude be in front of the "source"?

-avz --exclude "docs/" /home.... ?

> **DGortze380 said:**
> You can easily put those in a script and load the script into cron to run automatically in the background whenever you want.
Or running it at startup or during shutdown...

---

### Post by whorush on 2008-08-15
it works with the exclude flag at the end.

i thought about cron'ing it up, but i'll just do it manually.

---

