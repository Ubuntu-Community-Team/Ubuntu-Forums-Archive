---
title: "size of free space on hdd does not make sense"
date: 2009-10-13
forum: Hardware
---

### Post by frazerr on 2009-10-13
I have a 16gb hard drive
when I click on its properties - the results I get are confusing.

The drive has my home folder, nothing else, and this is 1.3 GB - but for some reason the disk properties say 4.4GB are being used.

and its a 16GB drive, but the properties say it is 14.4GB

I have included a screen shot


is there some way to scan the disk for errors?

any other suggestions or explanations?

thanks

---

### Post by frazerr on 2009-10-18
any suggestions?

---

### Post by WestCity on 2009-10-18
14.4GB is real size of 16GB HDD. In example: if U buy a 320GB HDD, it will be only ~300GB in real.

---

### Post by frazerr on 2009-10-18
thanks.  


so any idea why my 1.3GB of data was showing up as 4Gb?

oh - just checked it  -  it now shows as 7GB.
I put some big files on and deleted them...

I used rm to delete them, and just to be clear I have emptied the recycle bin.

why is this space still taken up?

---

### Post by WestCity on 2009-10-18
I'm not sure, if it will help...but you can try to run "System -> Administration -> Computer Janitor".

---

### Post by drs305 on 2009-10-18
Have you deleted any files as 'root'? Root has it's own trash bin and it's trash is not deleted when you empty your own bin.

You can take a look at the Disk Space link in my signature line, which includes methods to detect what is taking up space. There is also a link on that page to a guide on Trash that I wrote a while back. The answer is probably on one or both of those pages.

Additionally, the system reserves 5% of the disk space for system use. That amount is tweakable but should probably not be changed on a partition of your size. The details are also in the guide.

---

### Post by frazerr on 2009-10-18
> **drs305 said:**
> Have you deleted any files as 'root'? Root has it's own trash bin and it's trash is not deleted when you empty your own bin.

You can take a look at the Disk Space link in my signature line, which includes methods to detect what is taking up space. There is also a link on that page to a guide on Trash that I wrote a while back. The answer is probably on one or both of those pages.

Additionally, the system reserves 5% of the disk space for system use. That amount is tweakable but should probably not be changed on a partition of your size. The details are also in the guide.

thanks.

so everything in your DiskSpace Link seemed to give me the 3.8Gb.
nothing other than disk properties says there is 7gb

I did find one weird thing I didnt understand:

sudo du -h --max-depth=1 
du: cannot access `./home/frazer/.gvfs': Permission denied
du: cannot access `./home/frazer/.Skype/shared.xml': Stale NFS file handle
du: cannot access `./home/frazer/.dropbox/cache/l/4ad6ea0f': Stale NFS file handle
du: cannot access `./home/frazer/.dropbox/cache/l/4ad6ed5f': Stale NFS file handle
3.8G	./home

could those be the weird hidden things taken up disk space?

and thanks for showing me Disk Usage Analyzer.  That tool is awesome.

---

