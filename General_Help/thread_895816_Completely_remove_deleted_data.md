---
title: "Completely remove deleted data"
date: 2008-08-20
forum: General Help
---

### Post by colobix on 2008-08-20
How can I completely remove all the deleted data so I can save space. Is that possible.

Thanks:)

---

### Post by finer recliner on 2008-08-20
if you use the 'rm' command to delete files, your files are already gone forever and the free space is recovered for new files to be stored.

if you move files to the trash, just right click on the trash folder in the lower right hand corner and click "empty trash"

---

### Post by davidpeace on 2008-08-20
I've used rm to remove files and it doesn't always completely remove them. For example, before a clean install, I used apt-get remove to get rid of firefox, but strangely enough, I was still able to run it. I then searched for firefox files and rm'ed a lot of them but many of them still hung around, even with the sudo. I don't have firefox now (using Seamonkey) because I used the apt-get but I have checked and there are still a lot of firefox files laying around. Fortunately, I'm not hard up for space yet, but I'm wondering if there is a better way... Thanks.:confused:

---

### Post by colobix on 2008-08-20
The files won't be really deleted then. Only compressed and numbered to be overwritten later.
But thanks anyway.

I would like to know how I can deleted the recoverable data i've already deleted-

---

### Post by finer recliner on 2008-08-20
> **davidpeace said:**
> I've used rm to remove files and it doesn't always completely remove them. For example, before a clean install, I used apt-get remove to get rid of firefox, but strangely enough, I was still able to run it. I then searched for firefox files and rm'ed a lot of them but many of them still hung around, even with the sudo. I don't have firefox now (using Seamonkey) because I used the apt-get but I have checked and there are still a lot of firefox files laying around. Fortunately, I'm not hard up for space yet, but I'm wondering if there is a better way... Thanks.:confused:

try ```
sudo apt-get purge *package*
``` next time. see the man page for apt-get for more info.

---

### Post by finer recliner on 2008-08-20
> **colobix said:**
> The files won't be really deleted then. Only compressed and numbered to be overwritten later.
But thanks anyway.

I would like to know how I can deleted the recoverable data i've already deleted-

please give us more information. the ext3 filesystem (one of the more common filesystems that linux users use) was not designed to be able to recover data after being deleted.

why do you think you can recover deleted files? and why do you think your space is not being freed up after deleting a file?

---

### Post by paul382 on 2008-08-28
You can delete data using rm command or using above mentioned method. But these methods doesn't delete data completely and theses data can be recover with the help of data recovery softwares. To completely erase data you need help of some [drive wipe]("http://www.drive-wipe.com") software which will overwrite the data so that data can't be recovered

---

### Post by Ryadt on 2008-08-28
You don't need any software. Use the 'shred' command.
[http://linux.about.com/library/cmd/blcmdl1_shred.htm](http://linux.about.com/library/cmd/blcmdl1_shred.htm)

---

### Post by Too Late on 2008-08-28
There seems to be a "secure-delete" package in Synaptic, which should be able to do the things mentioned above. I've never used that, though.

edit: Ok, that shred command looks fine, too.

---

