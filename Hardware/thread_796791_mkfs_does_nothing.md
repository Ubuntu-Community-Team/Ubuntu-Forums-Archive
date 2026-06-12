---
title: "mkfs does nothing"
date: 2008-05-16
forum: Hardware
---

### Post by awacs on 2008-05-16
installed a new USB hard disk (1TB), comes right up.
I can even mount it - it shows various windows files, etc.
I wouldn't mind using it like that, except that it keeps complaining 'read-only file system', no matter what i do, or what options i pass.

so, i fdisk the drive, replace the windows partition, with a Linux one, then run mkfs - it takes HOURS, but spits out
the usual output 'writing inode tables: 2469/7453' ...
and finishes.

Then i mount the drive, and - voila! - the windows stuff
is still there. 

So, *what* am I missing?

Thanks!

---

### Post by starcannon on 2008-05-16
sudo apt-get install gparted

then go to System-Administration-Partition Editor

A nice gui that lets you delete, resize, format, partitions will pop up, I use this all the time and really like it a lot. It doesn't give me permissions issues when finished either. Anyway, maybe try that tool, its a bit more intuitive and will likely get you where you want to be.

---

