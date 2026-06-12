---
title: "tar while retaining permission/ownership, and wildcards in places file."
date: 2008-11-26
forum: General Help
---

### Post by Phases on 2008-11-26
Every night I have a backup running on my server, using the following command:

tar -cvf /media/backup_drive/backups/$(date +%Y_%m_%d).tar -T /media/backup_drive/backups/places_nightly > /media/backup_drive/backups/logs/$(date +%Y_%m_%d).log

Which, obviously I guess, makes a backup tar file with the date as the name, using a text file to define what all to backup - and makes a log with the date too. 

My places_nightly looks something like:

/path/to/directory
/another/directory
/yet/another
/path/to/file
/path/to/file2

I discovered not too long ago when installing the new server that tar'ing up a buncha stuff and moving over doesn't keep the permissions, and caused me a little bit of a headache. Hence, this post. 

I found this:

[http://lists.evolt.org/archive/Week-of-Mon-20001225/022252.html](http://lists.evolt.org/archive/Week-of-Mon-20001225/022252.html)

However, I'm having a little trouble looking at his command and comparing it to mine. 
 
Can someone help me figure out what I need to use exactly?

Also, on a side note: I just glanced at last nights log since I added some stuff yesterday. It appears I can't put something like this in the places file(?): /path/to/multiple/similiar/files*

It didn't backup any of the files using the wildcard.

(Edit: I'm at work right now so I can't check  but, maybe it tars and keeps the permissions, and it's the untarring that's changing them to root?)

---

### Post by sdennie on 2008-11-26
Tar should indeed keep the permissions.  You can check to see if your permissions problems are from the tar or the untar with:

```

tar tvf some_file.tar

```

---

### Post by Phases on 2008-11-26
Hey, thanks for the reply. 

Ok, you're right, that shows everything with the correct permissions. So, my problem is when I untar? 

I guess I could wait until the time comes that I need to do it (hopefully never) but, how would I do that? I assume something with umask 0, but not sure.

---

### Post by sdennie on 2008-11-26
Odd, the man page for tar says --same-permissions and --same-owner is the default for root.  What command are you using to extract the tar file that causes them to become root owned?

---

### Post by Phases on 2008-11-26
I just used..
```
tar -xf file.tar
```

It was a restore to a new system.. does that matter?

---

### Post by sdennie on 2008-11-26
That looks correct to me.  I'm not sure what the problem is.

One thing I might suggest would be rather than directly using tar and cron for your backups, instead use sbackup.  It accomplishes the same thing you are doing (even ends up using tar) but, it's a bit easier to use.

---

### Post by Phases on 2008-11-26
Hmm..

Ok well, thanks for your help. :)

---

